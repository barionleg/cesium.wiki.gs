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
   * Combing geometries is effective for static data, not necessarily for dynamic data.

Let's rewrite the code example above using geometries and appearances:
```javascript
var instance = new GeometryInstance({
  geometry : new ExtentGeometry({
    extent : Extent.fromDegrees(0.0, 20.0, 10.0, 30.0)
  })
});

var extentPrimitive = new Primitive({
  geometryInstances : instance,
  appearance : new EllipsoidSurfaceAppearance({
    material : Material.fromType(scene.getContext(), 'Dot')
  })
});

scene.getPrimitives().add(extentPrimitive);
```

Instead of using the explicit [ExtentPrimitive](http://cesium.agi.com/Cesium/Build/Documentation/ExtentPrimitive.html) type, we used the generic [Primitive](http://cesium.agi.com/Cesium/Build/Documentation/Primitive.html), which combined the geometry instance and appearance.  For now, we will not differentiate between a geometry and a geometry instance other than an instance is a container for a geometry.

To create the geometry for the extent, i.e., the triangles covering the rectangular region and fit the curvature of the globe, we create an [ExtentGeometry](http://cesium.agi.com/Cesium/Build/Documentation/ExtentGeometry.html).

**TODO: wireframe screenshot**

Since we know is on the surface, we use the [EllipsoidSurfaceAppearance](http://cesium.agi.com/Cesium/Build/Documentation/EllipsoidSurfaceAppearance.html), which is able to save memory and support all materials given that the geometry is on the surface - or at a constant height.

## Combing Geometries

We see the performance benefit when we use the same primitive to draw multiple geometries.  For example, let's draw two rectangles.
```javascript
var instance = new GeometryInstance({
  geometry : new ExtentGeometry({
    extent : Extent.fromDegrees(0.0, 20.0, 10.0, 30.0)
  })
});

var anotherInstance = new GeometryInstance({
  geometry : new ExtentGeometry({
    extent : Extent.fromDegrees(0.0, 40.0, 10.0, 50.0)
  })
});

var extentPrimitive = new Primitive({
  geometryInstances : [instance, anotherInstance],
  appearance : new EllipsoidSurfaceAppearance({
    material : Material.fromType(scene.getContext(), 'Dot')
  })
});

scene.getPrimitives().add(extentPrimitive);
```
Here we created another [GeometryInstance](http://cesium.agi.com/Cesium/Build/Documentation/GeometryInstance.html) with a different extent, and then provided both instances to the primitive.

This requires that both instances are drawn with the same appearance.  Some appearances allow each instance to provide unique attributes.  In particular we can use [PerInstanceColorAppearance](http://cesium.agi.com/Cesium/Build/Documentation/PerInstanceColorAppearance.html), to shade each instance with a different solid color.
```javascript
var instance = new GeometryInstance({
  geometry : new ExtentGeometry({
    extent : Extent.fromDegrees(0.0, 20.0, 10.0, 30.0)
  }),
  color : new Color(1.0, 0.0, 0.0, 0.5)
});

var anotherInstance = new GeometryInstance({
  geometry : new ExtentGeometry({
    extent : Extent.fromDegrees(0.0, 40.0, 10.0, 50.0)
  }),
  color : new Color(0.0, 0.0, 1.0, 0.5)
});

var extentPrimitive = new Primitive({
  geometryInstances : [instance, anotherInstance],
  appearance : new PerInstanceColorAppearance()
});

scene.getPrimitives().add(extentPrimitive);
```
Above, each instance has a [Color](http://cesium.agi.com/Cesium/Build/Documentation/Color.html) and the primitive is now constructed with `PerInstanceColorAppearance`, which knows to use the per-instance color for shading, instead of using a material.

TODO: list of geometries and appearances
TODO: matching geometries and appearances
TODO: why instances
TODO: pickData
TODO: updating per-instance show/color/attribute

## Resources

In the reference documentation, see:

* [All geometries](http://cesium.agi.com/Cesium/Build/Documentation/index.html?filter=Geometry)
* [All appearances](http://cesium.agi.com/Cesium/Build/Documentation/index.html?filter=Appearance)
* [Primitive](http://cesium.agi.com/Cesium/Build/Documentation/Primitive.html)
* [GeometryInstance](http://cesium.agi.com/Cesium/Build/Documentation/GeometryInstance.html)

If you have questions, post them to the [forum](http://cesium.agi.com/forum.html).

# Part II: Creating Custom Geometry and Appearances

# Part III: Geometry Batching for Vector Data Rendering