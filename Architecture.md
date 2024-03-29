**This is now out-of-date.  There will be a new version as part of [#1683](https://github.com/AnalyticalGraphicsInc/cesium/issues/1683).  In the meantime, see [Graphics Tech in Cesium - The Graphics Stack](http://cesiumjs.org/2015/05/26/Graphics-Tech-in-Cesium-Stack/)**

<!-- More links to specific parts of the reference documentation and Sandbox -->

Cesium is a client-side virtual globe and map library written in JavaScript using WebGL.  The Cesium stack is coarsely organized and composed of four layers:

<img src="architectureFigures/clientStack.png" width="50%" />

Generally, each layer adds functionality, raises the level of abstraction, and depends on the layers underneath it.  The layers are:
* _Core_ - number crunching like linear algebra, intersection tests, and interpolation.
* _Renderer_ - a thin abstraction over [WebGL](http://www.khronos.org/webgl/).
* _Scene_ - globe and map constructs like imagery layers, polylines, labels, and cameras.
* _Dynamic Scene_ - Time-dynamic visualization constructs including [CZML](CZML-Guide) rendering.

Each layer corresponds to one directory in the [source tree](https://github.com/AnalyticalGraphicsInc/cesium/tree/master/Source).  All layers are available to applications built using Cesium.  All apps use Core.  As shown below, a small subset of apps use Renderer directly, many apps use Scene directly, and perhaps the most apps, such the Cesium Viewer, use Dynamic Scene.

<img src="architectureFigures/invertedPyramid.png" width="50%" />

The following sections provide an overview of each layer.  For details on specific types, see the [reference documentation](http://cesiumjs.org/Documentation/).  For editable example code, see the [Sandbox](http://cesiumjs.org/Sandbox/Examples/Sandbox/).

<div id="core">
## Core

<img src="architectureFigures/core.png" width="30%" align="right" />

Core is the lowest layer in Cesium, and contains low-level, widely-used functions mostly related to math.  Examples include:
* Matrices, vectors, and quaternions.
* Transformations, such as cartographic to Cartesian.
* Map projections, such as Mercator and Equidistant Cylindrical.
* Sun position.
* Julian dates.
* Splines for interpolating position and orientation.
* Geometric routines like triangulation, subdivision surfaces, vertex cache optimization, and computing ellipse boundary points.

For example, the following code converts a cartographic point on the WGS84 ellipsoid at (0.0, 0.0), in radians, to Cartesian, that is, it converts from longitude/latitude to xyz:
```javascript
var ellipsoid = Ellipsoid.WGS84;
var p = ellipsoid.cartographicToCartesian(new Cartographic(0.0, 0.0));
```
The example below computes boundary points for an ellipse defined by a center point, two radii, and a bearing angle, on the WGS84 ellipsoid.
```javascript
var ellipsoid = Ellipsoid.WGS84;
var center = ellipsoid.cartographicToCartesian(new Cartographic(0.0, 0.0));
var bearing = CesiumMath.toRadians(60.0); // Cesium uses radians everywhere.
var positions = Shapes.computeEllipseBoundary(ellipsoid, center, 500000.0, 300000.0, bearing);
```

<div id="renderer">
## Renderer

See [Graphics Tech in Cesium - Renderer Architecture](http://cesiumjs.org/2015/05/15/Graphics-Tech-in-Cesium-Architecture/).

<div id="scene">
## Scene

<img src="architectureFigures/scene.png" width="30%" align="right" />

Scene builds on Core and Renderer to provide relativity high-level map and globe constructs, including:
* 3D globe, 2D map, and 2.5D columbus view all with one API.
* Streaming high-resolution imagery from multiple sources, including Bing Maps, Esri ArcGIS MapServer, OpenStreetMap, and Web Map Service (WMS).
* Polylines, polygons, billboards, labels, ellipsoids, and sensors.
* Materials that describe appearance.
* Cameras that control the view and respond to input.
* Animations that change properties over time.

<p align="center">
<img src="architectureFigures/sceneOverview.png" />
</p>

Scene represents all the graphical objects and state for canvas; there is a one-to-one relationship between a scene and a canvas:
```javascript
var scene = new Scene(document.getElementById("canvas"));
```
A scene can be 3D, 2D, or columbus view.  A scene can morph between these views with one line of code.

Primitives are objects added to the scene that are drawn.  Their implementation uses Renderer to make WebGL calls.  `Scene.render` has three major steps:
* Initialization: Sets the state of the current frame.
* Update: Primitives sync their state with Renderer resources such as vertex buffer and textures.
* Render: Issue draw calls for each primitive.

```javascript
(function tick() {
    scene.initializeFrame();
    // Insert app-specific animation code here.
    scene.render();
    requestAnimationFrame(tick);
}());
```
The `CentralBody` primitive represents the globe (in a future Cesium version, any central body such as the Moon and Mars will be supported).  High-resolution imagery from various servers is added using tile imagery providers.
```javascript
var layers = centralBody.getImageryLayers();
var newLayer = layers.addImageryProvider(new OpenStreetMapImageryProvider({
    url : 'http://otile1.mqcdn.com/tiles/1.0.0/osm/',
    proxy : new DefaultProxy('/proxy/')
});
newLayer.alpha = 0.5;
```
Materials represent the appearance of an object.  Currently, they can be applied to polygons and sensors.  Loosely speaking, materials are implemented as a GLSL shader function and a set of uniforms.
```javascript
polygon.material = Material.fromType(scene.getContext(), 'Stripe');
```
There are many built-in materials, and new ones can be scripted using [[Fabric]], a JSON schema, and GLSL.

Camera represents the view into the virtual world.  Ultimately, it creates a view matrix that transforms from world to eye coordinates.  Camera can be manipulated directly, but is most often updated via the `CameraController` for common tasks. The camera is modified automatically based on mouse or touch input by the scene's `ScreenSpaceCameraController`.

<div id="dynamicscene">
## Dynamic Scene

<img src="architectureFigures/dynamicScene.png" width="30%" align="right" />

Dynamic Scene builds on top of the previous three layers to enable data-driven visualization, primarily via the processing of CZML, a new JSON based schema for describing a time-dynamic graphical scene.

Rather than manually update primitives every frame, Dynamic Scene allows us to load or stream our data into a collection of high-level `DynamicObject`s, which are then rendered using Visualizers.  A single update call is all that's required to update the entire scene to a new time.

The code below is all that's needed to load and visualize any non-streaming CZML document into any Cesium based application.

```javascript
//Create a scene
var scene = new Scene(document.getElementById("canvas"));
//Create a DynamicObjectCollection to contain the objects from CZML
var dynamicObjectCollection = new DynamicObjectCollection();
//Create the standard CZML visualizer collection
var visualizers = VisualizerCollection.createCzmlStandardCollection(scene, dynamicObjectCollection);
//Create a Clock object to drive time.
var clock = new Clock();
//Download and parse a CZML file asynchronously
var czmlUrl = 'http://cesiumjs.org/someFile.czml';
getJson(czmlUrl).then(function(czml) {
    //Process the CZML, which populates the collection with DynamicObjects
    processCzml(czml, dynamicObjectCollection, czmlUrl);
    //Figure out the time span of the data
    var availability = dynamicObjectCollection.computeAvailability();
    clock.startTime = availability.start;
    clock.stopTime = availability.stop;
});
```
After the initial set-up, we call `update` in our `requestAnimationFrame` callback.

```javascript
var currentTime = clock.tick();
visualizers.update(currentTime);
```

While the above example is only nine lines of code ignoring comments, there's obviously a lot of work being done under-the-hood to parse and visualize the data.  There's also plenty of room for extending and customizing behavior for each use case.  The primary concept not seen in the above code is `DynamicObject`, which are created by the call to `processCzml` and populate the `dynamicObjectCollection`.  These object in turn, contain instances of `DynamicProperty`, which map to a CZML standard object and in most cases have a direct analogue to a Cesium primitive, e.g., `Billboard`.  For example, the code below gets all of the objects in the collection, sees if they have a `DynamicBillboard` instance with a `DynamicProperty` indicating scale, and retrieves the scale value for the current time.

```javascript
var dynamicObjects = dynamicObjectCollection.getObjects();
for (var i = 0, len = dynamicObjects.length; i < len; i++) {
    var dynamicBillboard = dynamicObject[i].billboard;
    if (typeof dynamicBillboard !== 'undefined') {
        var scale = dynamicBillboard.scale;
        if (typeof scale !=== 'undefined') {
            var currentScale = scale.getValue(currentTime);
        }
    }
}
```
Even though the above code isn't very useful on it's own, it's easy to see how an object could be written which maintains a `BillboardCollection` primitive that mirrors the data in the `dynamicObjectCollection` at a given time; in fact this is exactly what `DynamicBillboardVisualizer` does and it is a member of the standard `VisualizerCollection` created by the method of a similar name in the first example.

A full overview of CZML, including its structure and schema, as well as an in-depth overview of the Cesium client-side implementation, can be found in the [[CZML Guide]].