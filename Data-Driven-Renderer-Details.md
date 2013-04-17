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
      * Probably needs multi-frustum, but needs performance too.  How far can we push out the near plane?
   * Cube map passes for reflections and refractions in the final pass, one per cube map face
      * Low resolution?
      * Low geometric LODs?  Low shader LODs?
      * Only include select primitives, e.g., only the environment, only nearby models, etc.
      * Probably needs multi-frustum, but needs performance too.  
   * Terrain loading should only use the color frustum, not frustums from shadow and cube-map passes.
* Script-driven [post-processing effects](Screen-Space-Rendering-Details) such as motion blur and AO
* Handle dependencies, for example:
   * Motion blur requires the velocity buffer output by models.
   * Multi-pass algorithms like old-school outlined polylines and rendering the depth-plane after the central body.
* Minimize allocations to minimize GC pressure (not a feature, but still important)

What is a data-driven renderer and how does it help us achieve these goals?

In a nutshell, we remove `render` and have `update` return an object representing the draw calls `render` would have issued.  This allows the rendering engine to sort those calls, cull them, etc.  The process is data-driven.  For example, currently, if a primitive such as a model has several draw calls, the primitive would need code to cull each one, but with the data-driven approach, it can just return its draw calls, and let the renderer deal with them.

When designing our renderer, beware of the [architect astronaut](http://www.joelonsoftware.com/articles/fog0000000018.html).  They love over-engineering things.

We'll merge into master after each phase.

## _Done:_ Phase One: Add Culling

* _Done:_ Add view frustum and occlusion culling to existing primitives.  If a primitive returns a bounding volume in `update`, the scene automatically handles culling.
* _Done:_ Compute bounding spheres for 3D, 2D, and Columbus view.  Work correctly when morphing.  Balance sphere computation speed vs. tightness, e.g., do we recompute the entire sphere when one billboard is added to a `BillboardCollection`?

## _Done:_ Phase Two: Cleanup Picking

* _Done:_ Rename `SceneState` to `FrameState`.  It is more precise.
* _Done:_ Remove `updateForPick`.  Instead `FrameState` can contain a `Passes` object with a boolean per pass (or an array of booleans or whatever.  In C++, I would use a bitmask.)  The only pass will be `pick` for now.  When it's true, it will be as if `updateForPick` was called.
   * Later, we will expand `Passes` to include z-only passes for early-z and shadow maps, and cube-map passes for building cube-maps.  We could make each of these a separate `update` function, but I think keeping them together limits the amount of state a primitive has to keep around, e.g., a primitive doesn't have to compute something temporary in `update`, save it in a member, and then use it in `updateForCubeMapPass`.
* _Done:_ Create an off-center view frustum containing the picked pixel(s) so culling is much more effective.  Use this frustum for culling, but still render with the original frustum, i.e., the perspective matrix is still derived from the original frustum.  See my [Picking using the Depth Buffer](http://blogs.agi.com/insight3d/index.php/2008/03/05/picking-using-the-depth-buffer/).
* Later, we will scissor out the picked pixel to reduce the fragment load.  We'll need to modify everyone's render state, so we need their draw calls for that.

## _Done:_ Phase Three: Remove `render` and `renderForPick`

* _Done:_ Since current `render` functions don't have logic or their logic can easily be moved to `update`, remove `render` and `renderForPick`, and make `update` return an array of data for each draw call to make on the primitive's behalf, i.e., a `commandList`.  For example:
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
  // Ignoring frameState.Passes.pick...
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

`FrameState.Passes` will need a separate `color` or `final` pass so we don't overload `!pick` to mean `color`.

There are a ton of allocations, don't worry; we'll fix that soon.  This also kinda sucks for terrain, who will need to duplicate its uniforms per draw call to implement RTC for now.

This returns one list of commands.  Later the list will be a tree, and we'll have different trees for each requested pass.

## _Done:_ Phase Four: Multi-Frustum

Now that we have the command list, we can start doing useful things without requiring any additional code in the primitives.  First, let's add multiple frustums so we can virtually have an infinitely close near plane and an infinitely distant far plane without z-fighting.

Notes:
* Traditionally, for a 24-bit fixed-point depth buffer, a far-to-near ratio of 1,000 is good.  The guaranteed minimum bits in WebGL is 16.  I suspect most desktop implementations have 24 bits.  Tegra 3 has 16 bits, perhaps 16 is standard on most mobile devices.
   * Depending on the minimum triangle separation, 1,000 is probably very conservative.  For terrain tiles, it could be much higher.  However, objects need to interact with each other, e.g., terrain is not just depth tested against terrain; it is also depth tested against models, etc.
* Pushing out the near plane minimizes the total number of frustums needed.
* Fog allows users to pull in the far plane to minimize the total number of frustums needed.
* Instead of overlapping the frustums, perhaps we can fill the cracks by blurring them (not my idea, but I dig it).

We'll keep `near` and `far` exposed.  These will be worse-case values.  We'll dynamically compute near and far based on the bounding volumes when calling `update` for each primitive.  If a bounding volume intersects the near plane, we'll use the user-defined `near` value; if a bounding volume is `undefined`, we'll use the user-defined `near` and `far` (sucks I know, other ideas?); and so on.

Instead of culling like "for each frustum, for each primitive, cull against current view frustum", Deron had an idea a while back that is like "for each primitive, cull against left/bottom/right/top. for each remaining primitive, cull against near/far."  This allows us to cull a bunch of primitives before fully computing the dynamic near and far distances.  I extend this to cull against the user-defined near plane, so later we can discard based on the far distance only.

The algorithm looks something like this (careful, I didn't actually run this code):
```
var commands = [];  // Too many allocations, I know.
var near = /* ... */;
var far = /* ... */;

for each p in primitives {
  var cmds = p.update(/* ... */);
  if (typeof cmds !== 'undefined') {
    for each c in cmds {
      if (c.boundingVolume not culled by left/bottom/right/top/user-defined near) {
        commands.push(c);
        // Update near/far based on c.boundingVolume
      }
    }
  }
}

// Compute number of frustums
// Clear color
for each f in frustums back-to-front {
  // Clear depth
  // Compute projection matrix based on f
  for each c in commands {
    // The fields on c are computed based on the boundingVolume, which could be undefined.
    
    // Culled by current frustum's far plane
    if (c.nearestDistanceToViewer > f.far) {
      // discard c.  If commands is a linked list, we can remove it.  Don't bother until the command tree.
    }

    if (c.farthestDistanceToViewer < f.near) {
      // Culled by current frustum's near plane.  Skip it for now, 
      // but do not discard it since it will be rendered in a later frustum.
      continue;
    }
    
    // execute c

    if (c.nearestDistanceToViewer > f.near)) {
      // discard c since it isn't need in any future frustums.
    }
    // else intersects near plane of this frustum, needed in one or more future frustums.
  }
}

// render screen-space passes
```

`ViewportQuad` has an `undefined` bounding volume so we'll want to treat it separately to avoid using the extreme near and far distances.  We can introduce `overlay` and `overlayPick` passes.

We'll also need some stats so we know how many times each primitive is drawn per frame.

Other ideas:
* _Done:_ Use temporal coherence: speculatively use the frustum partitioning from the previous frame, while computing near/far for the current frame.  If the near/far for the current frame is way different, recompute.
* Can we quickly bin primitives into frustums?
* Can we partition the frustums to minimize translucent/expensive primitives that intersect multiple frustums?  What do we do with large primitives like sensors?  Use surface area heuristics (SAH) to select splitting planes?
* When zoomed-in ground level with terrain, lots of tiles will overlap the first and second frustum.  How can we improve performance?
* Down the road, can we exploit the parallelism of each each frustum and build each command queue separately.

## Phase Five: Command Tree

TODO
* Rename `update` to `buildCommandTree`?

## Phase n: Reduce allocations

TODO

## Later Phases

* Callback functions as commands?  Could be used to call WebGL directly.
* _Done_: Scissor out pick rectangle
* Picking optimizations: `color` and `pick` in the same pass.  Preserve pick color buffer between frames for static scenes.
* Automatically disable color buffer writes for early-z and shadow passes.
* [Post-processing](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Screen-Space-Rendering-Details) - color per frame, depth per frustum?
* Shadows
   * [Shadows for Real-Time Rendering](http://cis565-fall-2012.github.com/lectures/10-24-Shadows.pptx)
   * [Soft Shadow Mapping](http://codeflow.org/entries/2013/feb/15/soft-shadow-mapping/)

## Resources

* [Order your graphics draw calls around!](http://realtimecollisiondetection.net/blog/?p=86/)
* [Renderstate change costs](http://home.comcast.net/~tom_forsyth/blog.wiki.html#%5B%5BRenderstate%20change%20costs%5D%5D)
* [nulstein v2 plog - rendering overview](http://software.intel.com/en-us/blogs/2010/11/26/nulstein-v2-plog-rendering-overview/)
* [Some more frustum culling notes](http://fgiesen.wordpress.com/2010/10/20/some-more-frustum-culling-notes/)
* [Renderer Design](http://diaryofagraphicsprogrammer.blogspot.com/2007/12/renderer-design.html)
* Designing a Data-Driven Renderer in [GPU Pro 3](http://gpupro3.blogspot.com/)
* Chapter 6 in [3D Engine Design for Virtual Globes](http://www.virtualglobebook.com/)