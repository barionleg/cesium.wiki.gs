This is a draft for a three-part blog series.  The first two are Cesium tutorials.  The last is a general graphics tech article.

_Links to the reference doc don't work yet._

# Part I: Geometry and Appearances

Cesium has a library of primitives, like polygons and ellipsoids, that are the visual building blocks of our scene.  To use them, we create the primitive and give it position data and perhaps a [material](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Fabric).  For example, the following creates a rectangle on the globe with a dot pattern:

```javascript
var extentPrimitive = new ExtentPrimitive({
  extent : Extent.fromDegrees(0.0, 20.0, 10.0, 30.0),
  material : Material.fromType(scene.getContext(), 'Dot')
});
scene.getPrimitives().add(extentPrimitive);
```

**TODO: screenshot**

In this tutorial, we go under the hood of primitives and look at the [Geometry](http://cesium.agi.com/Cesium/Build/Documentation/Geometry.html) and [Appearance](http://cesium.agi.com/Cesium/Build/Documentation/Appearance.html) types that power them.  The benefits of using geometries and appearances directly are:
* **Performance** - when drawing a large number of static primitives, e.g., polygons for all the zip codes in the United States, using geometries directly allows us to combine them into a single geometry to reduce CPU overhead and better utilize the GPU.  **TODO: performance numbers.**
* **Flexibility** - Primitives combine geometry, i.e., the triangles, lines, and points composing an object, and appearance, i.e., the GLSL shaders and render state that shade an object.  By decoupling them, we can modify them independently.  We can:
   * Add new geometries that are compatible with many different appearances.
   * Add new appearances that are compatible with many different geometries.
* **Low-level Access** - Appearances provide close-to-the-metal access to rendering without having to worry about all the details of using the [Renderer](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture#renderer) directly.  Appearances make it easy to:
   * Write full GLSL vertex and fragment shaders.
   * Modify the render state.

There are also some downsides:
   * Using geometries and appearances directly requires slightly more code and a deeper understanding of graphics.  Primitives are at the level of abstraction appropriate for mapping apps; Geometries and appearances have a level of abstraction closer to a traditional 3D engine.
   * Combing geometries is effective for static data, not necessarily dynamic data.

**TODO: code example**



# Part II: Creating Custom Geometry and Appearances

# Part III: Geometry Batching for Vector Data Rendering