# Roadmap

We're always looking to:
* Write demos that showcase Cesium, especially demos that combine Cesium with other web APIs
* Support more content by writing converters from other formats to CZML using our [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer) library
* Write tutorials and improve reference documentation and examples
* Improve visual quality and performance - [details](Visual-Quality-and-Performance-Details)
* Improve platform support by fixing issues on various browsers, devices, or video cards
* Improve tests and test coverage; however, we don't blindly chase coverage statistics

## In progress
* [[CZML|Cesium Language (CZML) Guide]] Visualization
* Imagery layers - [details](Imagery-Layers-Details)
* Streaming terrain - [details](Streaming-Terrain-Details)
* Material system - [details](Material-System-Details)
* COLLADA models - [details](Models-Details)

## To come

If you are interested in implementing any of these features, start a discussion on the [mailing list](https://groups.google.com/d/forum/cesium-dev).

* Improve precision - remove jittering
* Data-driven renderer
   * Improved depth-buffer precision
   * Culling for all objects
   * Post-processing framework
* GLSL #include system - [details](GLSL-Details)
* Stars
* Draw shapes - ellipsoids, cylinders, boxes, extruded volumes
* Military symbol sets such as MS2525 and NTDS.  SVG files?
* Improve 3D/2D/Columbus view transitions
* Improve mobile support - consider [pointer.js](https://github.com/borismus/pointer.js)
* Support for multiple central bodies, i.e., Sun, Moon, etc.
* Build and test server
* Shadows
* Video on terrain
* Vectors
* Render buildings
* Label declutter
* Polyline and polygon LOD.  [Douglas-Peucker reduction](http://www.bowdoin.edu/~ltoma/teaching/cs350/spring06/Lecture-Handouts/hershberger92speeding.pdf)
* John Madden-style collaboration among multiple clients
* Particle system
* Ocean
* Volumetric clouds
* CZML
   * Layers
   * Path visualiztion
   * Improved materials support
   * Custom axes & reference frames
   * Buffer availability and "buffering" behavior
   * Imagery and terrain sources
   * Network links
   * Camera/Tours
   * Arbitrary link support (# and $ in CZML spec)
   * CZML defined user interfaces, possibly with markdown
   * Model support, once Cesium support exists
   * Z order support, once Cesium exists.
   * Human readable messages/events raised in CZML
* Widgets & Apps
   * OWF widget
   * Embeddable Cesium Viewer
   * Improved TimeLine widget
   * Standard Cesium toolbar
   * CZML Table of contents/Document Manager widget