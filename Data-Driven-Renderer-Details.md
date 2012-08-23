Design and implementation ideas for our data-driven renderer, e.g., no more explicit `render` functions.

Currently, the render loop has a classic and simple design: an `update` function for each primitive is called, which creates/modifies vertex buffers, textures, shaders, etc.  Then, each primitive's `render` function is called to issue draw calls.  This is a standard update/render setup, or perhaps animate/update/render since user code probably has an animation step that modifies the primitive's positions, etc. which are then synced with WebGL resources in `update`.

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
   * Cube Map passes for later reflections and refractions, one per cube map face
      * Low resolution?
      * Low geometric LODs?  Low shader LODs?
      * Only include select primitives, e.g., only the environment, only near by models, etc.
      * Probably needs multi-frustum
* Script-driven [post-processing effects](Screen-Space-Rendering-Details) such as motion blur and AO
* Handle dependencies, for example:
   * The motion blur postFX requires the velocity buffer output by models.
* Minimize allocations to minimize GC pressure (not a feature, but still important)

## _Done:_ Phase One: Add Culling

* _Done:_ Add view frustum and occlusion culling to existing primitives.  If a primitive returns a bounding volume in `update`, the scene automatically handles culling.
* _Done:_ Compute bounding spheres for 3D, 2D, and Columbus view.  Work correctly when morphing.  Balance sphere computation speed vs. tightness, e.g., do we recompute the entire sphere when one billboard is added to a `BillboardCollection`?

## Phase Two

## Resources

* [Order your graphics draw calls around!](http://realtimecollisiondetection.net/blog/?p=86/)
* [Renderer Design](http://diaryofagraphicsprogrammer.blogspot.com/2007/12/renderer-design.html)
* Designing a Data-Driven Renderer in [GPU Pro 3](http://gpupro3.blogspot.com/)
* [Renderstate change costs](http://home.comcast.net/~tom_forsyth/blog.wiki.html#%5B%5BRenderstate%20change%20costs%5D%5D)