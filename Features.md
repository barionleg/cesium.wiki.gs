<p align="center">
<img src="https://github.com/AnalyticalGraphicsInc/cesium/wiki/logos/Cesium_Logo_Color.jpg" width="50%" />
</p>

_Screen shots to follow soon..._

<!--
TODO: Images
TODO: Links
TODO: Animation changes values over time.
-->

## One API - Three Views

Cesium supports a 3D globe, 2D map, and Columbus view (2.5D) with the same API.  The scene can transition between views with one line of code.

## Geospatial Data Visualization

* Drawing dynamic scenes from [CZML](https://github.com/AnalyticalGraphicsInc/cesium/wiki/czml-guide).
* Drawing imagery from Bing, Esri, OpenStreetMap, and WMS.
* Drawing vector data from KML (partial support), ESRI Shapefiles, and WebGL Globe JSON.
* Drawing polylines, polygons, circles, ellipses, extents, billboards, labels, and sensors.
* Picking individual objects.
* Batching and GPU optimizations for performance.

## Apps Widgets

* [Cesium Viewer](http://cesium.agi.com/CesiumViewer/) app for visualizing CZML files.
* [Sandbox](http://cesium.agi.com/Sandbox/Examples/Sandbox/) app for live coding.
* Timeline widget for scrubbing through time.
* Cesium and timeline widget for use with Dojo.

Checkout all the [demos](http://cesium.agi.com/).

## Cameras

Cameras control the view and respond to input.

* Spindle - spin, zoom, and pan the globe.
* Flight - flies to a destination.
* Free look - look in any direction.

## Materials

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

* View frustum and occlusion culling (horizon culling).
* Vertex cache optimization.
* Polygon triangulation and subdivision.
* Tessellation of ellipsoids, extents, boxes, and planes.
* Bounding spheres and axis-aligned bounding boxes.

## Math

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

## Next Steps

Use the [Quick Start](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Quick-Start) to get up and running with Cesium, or read the [Architecture Overview](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture) to learn about the architecture and code.