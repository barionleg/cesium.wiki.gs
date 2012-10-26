<p align="center">
<img src="https://github.com/AnalyticalGraphicsInc/cesium/wiki/logos/Cesium_Logo_Color.jpg" width="50%" />
</p>

<!--
TODO: Animation changes values over time.
TODO: Links to full-size images.
TODO: Reference links?
-->

Cesium is a JavaScript virtual globe and map library written in JavaScript using [WebGL](http://www.khronos.org/webgl/).  It provides hardware-accelerated graphics in a browser without a plugin.

Cesium is built with care; code is peer-reviewed, unit tested, [statically analysed](http://www.jshint.com/), and [documented](http://cesium.agi.com/Documentation/).

## One API - Three Views

<img src="features/3D.png" width="200" height="100" alt="3D" />
<img src="features/2D.png" width="200" height="100" alt="2D" />
<img src="features/ColumbusView.png" width="200" height="100" alt="Columbus view" />

Cesium supports a 3D globe, 2D map, and Columbus view (2.5D) with the same API.  Transition between views with one line of code.

## Dynamic Geospatial Data Visualization

<a href="features/Nashville-Full.png"><img src="features/Nashville.png" width="268" height="100" alt="Nashville" /></a>
<img src="features/Cities.png" width="145" height="100" alt="World Cities" /><br />
<img src="features/sensors.png" width="176" height="99" alt="Sensors" />
<a href="features/ImageryLayers.jpg"><img src="features/ImageryLayersSmall.png" width="150" height="100" alt="Imagery Layers" /></a>

* Draw dynamic scenes from [CZML](https://github.com/AnalyticalGraphicsInc/cesium/wiki/czml-guide).
* Layer imagery from multiple sources, including WMS, OpenStreetMaps, Bing Maps, ArcGIS MapServer, and standard image files.  Each layer can be alpha blended with the layers below it.
* Draw vector data from KML (partial support), ESRI Shapefiles, and WebGL Globe JSON.
* Draw polylines, polygons, polygons with holes, circles, ellipses, extents, billboards, labels, ellipsoids, and sensors.
* Batching, culling, and JavaScript and GPU optimizations for performance.
* Precision handling for large view distances (avoiding [z-fighting](http://www.sjbaker.org/steve/omniv/love_your_z_buffer.html)) and large world coordinates (avoiding [jitter](http://blog.virtualglobebook.com/2010/11/vertex-transform-precision.html), partial support).
* Individual object picking.

<!-- For example, minimize GC pressure -->

## Apps and Widgets

* [Cesium Viewer](http://cesium.agi.com/CesiumViewer/) app for visualizing CZML files.
* [Sandbox](http://cesium.agi.com/Sandbox/Examples/Sandbox/) app for live coding.
* Timeline widget for scrubbing through time.
* Cesium and timeline widget for use with Dojo.

Checkout all the [demos](http://cesium.agi.com/).

## Cameras

<img src="features/CameraFlight.png" width="200" height="92" alt="Flight camera" />
<img src="features/CameraPan.png" width="200" height="92" alt="Panning with the spindle camera" />

Cameras respond to input and control the view.

* Spindle - spin, zoom, and pan the globe with inertia.
* Flight - flies to a destination.
* Free look - look in any direction.

## Materials

<img src="materials/CheckerboardCircle.png" width="200" height="92" alt="Checkerboard" />
<img src="materials/VerticalStripeCircle.png" width="200" height="92" alt="Vertical stripe" />
<img src="materials/DotCircle.png" width="200" height="92" alt="Dot" /><br />
<img src="materials/BrickCircle.png" width="200" height="92" alt="Brick" />
<img src="materials/WoodCircle.png" width="200" height="92" alt="Wood" />
<img src="materials/FacetCircle.png" width="200" height="92" alt="Facet" />

Materials describe the surface appearance of objects in the scene.

* Procedural textures - checkerboard, stripes, dots, brick, cement, asphalt, wood, grass, distance intervals, tie dye, ...
* Classic: diffuse map, specular map, alpha map, normal map, bump map, emission map, reflection, refraction, and Fresnel.
* [[Fabric]] - a JSON schema for describing and combing materials.

## Low-Level Rendering

For those needing custom drawing, Cesium contains a thin abstraction over WebGL that provides:

* Built-in GLSL uniforms for common transformations.
* Built-in GLSL functions for ellipsoids, rays, noise, lighting, Constructive Solid Geometry (experimental), ...
* Shader programs and caching.
* Textures and cube maps.
* Dynamic texture atlas packing.
* Buffers, vertex arrays, and vertex layout. 
* Render states.
* Framebuffers and renderbuffers.

## Geometric Routines

<img src="features/EllipsoidTessellator.png" width="108" height="92" alt="Ellipsoid tessellation" />
<img src="features/ExtentTessellator.png" width="108" height="92" alt="Extent tessellation" />

* View frustum and occlusion culling (horizon culling).
* Vertex cache optimization.
* Polygon triangulation and subdivision.
* Tessellation of ellipsoids, extents, boxes, and planes.
* Bounding spheres and axis-aligned bounding boxes.

## Math

<img src="features/EllipsoidTangentPlane.png" width="178" height="92" alt="Ellipsoid tangent plane" />

* Types for Cartesian, spherical, and cartographic positions.
* Types for matrices and quaternions.
* Catmull-Rom splines.
* Lagrange, Hermite, spherical linear, and linear interpolation.
* Sun position.
* Equidistant Cylindrical and Mercator 2D map projections.
* Computations on ellipsoids such as computing computing surface normals, circles, ellipses, and tangent planes.
* Transformations such as cartographic to Cartesian, east-north-up to fixed frame, and TEME to pseudo-fixed frame.

## Time 

* Julian dates, leap seconds, time intervals, and UTC and TAI time standards.

## Infrastructure

* JSONP.
* Generic event handling.

## Deployment
* Use a Cesium as a single js file or with Asynchronous Module Definition (AMD) to include only what you use.

## Next Steps

Use the [Quick Start](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Quick-Start) to get up and running with Cesium, or read the [Architecture Overview](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture) to learn about the code.

More questions?  See the [FAQ](https://github.com/AnalyticalGraphicsInc/cesium/wiki/FAQ).