Currently, the render loop has a classic and simple design: an `update` function on each primitive is called, which creates/modifies vertex buffers, textures, shaders, etc.  Then, each primitive's `render` function is called to issue draw calls.  This is a standard update/render setup, or perhaps animate/update/render since user code probably has an animation step that modifies the primitive's positions, etc. which are then synced with WebGL resources in `update`.

We'd like to add several features without burdening those implementing primitives:
* View frustum and occlusion culling
* Multi-frustum to avoid z-fighting
* Sorting
   * For correctness
      * Back-to-front for transparency
      * Z-order objects on the globe
   * For performance
      * Front-to-back for early-z
      * By framebuffer
      * By shader/material
* Multiple render passes
   * Z-prepass for performance
   * Shadow pass per shadow-casting light
      * Depth-only
      * Culling based on volume created by the view frustum and light direction
      * Probably needs multi-frustum
   * Cube map passes for reflections and refractions in the final pass, one per cube map face
      * Low resolution?
      * Low geometric LODs?  Low shader LODs?
      * Only include select primitives, e.g., only the environment, only nearby models, etc.
      * Probably needs multi-frustum
* Script-driven [post-processing effects](Screen-Space-Rendering-Details) such as motion blur and AO
* Handle dependencies, for example:
   * Motion blur requires the velocity buffer output by models.
   * Multi-pass algorithms like old-school outlined polylines and rendering the depth-plane after the central body.
* Minimize allocations to minimize GC pressure (not a feature, but still important)

What is a data-driven renderer and how does it help us achieve these goals?

In a nutshell, we remove `render` and have `update` return an object representing the draw calls `render` would have issues.  This allows the rendering engine to sort those calls, cull them, etc.  The process is data-driven.  For example, currently, if a primitive such as a model has several draw calls, the primitive would need code to cull each one, but with the data-driven approach, it can just return its draw calls, and let the rendering engine deal with them.

We should be able to merge into master after each phase.

## _Done:_ Phase One: Add Culling

* _Done:_ Add view frustum and occlusion culling to existing primitives.  If a primitive returns a bounding volume in `update`, the scene automatically handles culling.
* _Done:_ Compute bounding spheres for 3D, 2D, and Columbus view.  Work correctly when morphing.  Balance sphere computation speed vs. tightness, e.g., do we recompute the entire sphere when one billboard is added to a `BillboardCollection`?

## Phase Two: Cleanup Picking

* Rename `SceneState` to `FrameState`.  It is more precise.
* Remove `updateForPick`.  Instead `FrameState` can contain a `Passes` object with a boolean per pass (or an array of booleans or whatever.  In C++, I would use a bitmask.)  The only pass will be `Pick` for now.  When it's true, it will be as if `updateForPick` was called.
   * Later, we will expand `Passes` to include z-only passes for early-z and shadow maps, and cube-map passes for building cube-maps.  We could make each of these a separate `update` function, but I think keeping them together limits to amount of state a primitive has to keep around, e.g., a primitive doesn't have to compute something temporary in `update`, save it in a member, and then use it in `updateForCubeMapPass`.
* Create an off-center view frustum containing the picked pixel(s) so culling is much more effective.  Use this frustum for culling, but still render with the original frustum, i.e., the perspective matrix is still derived from the original frustum.  See my [Picking using the Depth Buffer](http://blogs.agi.com/insight3d/index.php/2008/03/05/picking-using-the-depth-buffer/).
* Later, we will scissor out the picked pixel to reduce the fragment load.  We'll need to modify everyone's render state, so we need their draw calls for that.

## Phase Three: Remove `render` and `renderForPick`

* Since current `render` functions don't have logic or their logic can easily be moved to `update`, remove `render` and `renderForPick`, and make `update` return an array of data for each draw call to make on the primitive's behalf, i.e., a `commandList`.  For example:
```javascript
foo.prototype.update = function(context, frameState) {
  return {
    boundingVolume : this._boundingVolume,
    modelMatrix : this.modelMatrix
  };
};

foo.prototype.render = function(context) {
  context.draw({
    primitiveType : PrimitiveType.TRIANGLES,
    shaderProgram : this._sp,
    uniformMap : this._drawUniforms,
    vertexArray : this._va,
    renderState : this._rs
  });
};
```
becomes
```javascript
foo.prototype.update = function(context, frameState) {
  // Ignoring frameState.Passes.Pick...
  return [{
    boundingVolume : this._boundingVolume,    // optional
    modelMatrix : this.modelMatrix,           // optional
    primitiveType : PrimitiveType.TRIANGLES,  // Here and below are arguments to Context.draw
    shaderProgram : this._sp,
    uniformMap : this._drawUniforms,
    vertexArray : this._va,
    renderState : this._rs
  }];

  // Or if we need to include a clear
  // return [{
  //  clearState : context.createClearState()
  // }];
};
```
Yes, there are a ton of allocate, don't worry; we'll fix that soon.  This also kinda sucks for terrain, who will need to duplicate its uniforms per draw call to implement RTC for now.

TODO: Callback functions as commands?

## Resources

* [Order your graphics draw calls around!](http://realtimecollisiondetection.net/blog/?p=86/)
* [Renderer Design](http://diaryofagraphicsprogrammer.blogspot.com/2007/12/renderer-design.html)
* Designing a Data-Driven Renderer in [GPU Pro 3](http://gpupro3.blogspot.com/)
* [Renderstate change costs](http://home.comcast.net/~tom_forsyth/blog.wiki.html#%5B%5BRenderstate%20change%20costs%5D%5D)