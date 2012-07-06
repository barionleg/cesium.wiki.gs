<p align="center">
<img src="https://github.com/AnalyticalGraphicsInc/cesium/wiki/logos/Cesium_Logo_Color.jpg" width="50%" />
</p>

<!--
TODO: Links
TODO: Animation changes values over time.
-->

Cesium is a JavaScript virtual globe and map library written in JavaScript using [WebGL](http://www.khronos.org/webgl/).  It provides hardware-accelerated graphics in a browser without a plugin.

Cesium is built with care; code is peer-reviewed, unit tested, [statically analysed](http://www.jshint.com/), and [documented](http://cesium.agi.com/Documentation/).

## One API - Three Views

Cesium supports a 3D globe, 2D map, and Columbus view (2.5D) with the same API.  Transition between views with one line of code.

## Dynamic Geospatial Data Visualization

* Draw dynamic scenes from [CZML](https://github.com/AnalyticalGraphicsInc/cesium/wiki/czml-guide).
* Draw imagery from Bing, Esri, OpenStreetMap, and WMS.
* Draw vector data from KML (partial support), ESRI Shapefiles, and WebGL Globe JSON.
* Draw polylines, polygons, circles, ellipses, extents, billboards, labels, and sensors.
* Batching and GPU optimizations for performance.
* Individual object picking.

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

<img src="features/CheckerboardMaterial.png" width="200" height="92" alt="Checkerboard" />
<img src="features/VerticalStripeMaterial.png" width="200" height="92" alt="Vertical stripe" />
<img src="features/DotMaterial.png" width="200" height="92" alt="Dot" /><br />
<img src="features/BrickMaterial.png" width="200" height="92" alt="Brick" />
<img src="features/WoodMaterial.png" width="200" height="92" alt="Wood" />
<img src="features/FacetMaterial.png" width="200" height="92" alt="Facet" />

Materials describe the surface appearance of objects in the scene.

* Procedural textures - checkerboard, stripes, dots, brick, cement, asphalt, wood, grass, distance intervals, tie dye, ...
* Classic: diffuse map, specular map, alpha map, normal map, bump map, emission map, reflection, refraction, and Fresnel.
* A JSON schema for combing materials.

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
* Transformations such as cartographic to Cartesian, and east-north-up to fixed frame.

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