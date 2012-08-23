# Roadmap

We're always looking to:
* Write demos that showcase Cesium, especially demos that combine Cesium with other web APIs
* Support more content by writing converters from other formats (GML, GeoJSON, ...) to CZML using our [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer) library
* Write tutorials and improve reference documentation and examples
* Improve visual quality and performance - [details](Visual-Quality-and-Performance-Details)
* Improve platform support by fixing issues on various browsers, devices, or video cards
* Improve tests and test coverage; however, we don't blindly chase coverage statistics

## In progress
* Sandcastle
* Imagery layers - [details](Imagery-Layers-Details)
* Streaming terrain - [details](Streaming-Terrain-Details)
* GeoServer CZML writer
* CZML External links - [details](External-links)
* CZML Path/History visualization - [details](Path-Visualization-Details)
* Screen Space Rendering - [details](Screen-Space-Rendering-Details)
* Data-Driven Renderer - [details](Data-Driven-Renderer-Details)
* COLLADA models - [details](Models-Details)

## To come

If you are interested in implementing any of these features, start a discussion on the [mailing list](https://groups.google.com/d/forum/cesium-dev).

* Improve precision - remove jittering
* GLSL #include system - [details](GLSL-Details)
* Stars
* Draw shapes - ellipsoids, cylinders, boxes, extruded volumes
* Military symbol sets such as MS2525 and NTDS.  SVG files?
* Improve 3D/2D/Columbus view transitions
* Improve mobile support - consider [pointer.js](https://github.com/borismus/pointer.js)
* Support standard web servers: WMTS, WFS, WCS, ...
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
* More material system improvements - [details](Material-System-Details)
* Compass - know where north is
* CZML
   * Z-ordering - [czml-writer issue](https://github.com/AnalyticalGraphicsInc/czml-writer/issues/20)
   * Buffer availability and "buffering" behavior
   * Layers
   * Improved materials support
   * Custom axes & reference frames
   * Imagery and terrain sources
   * Camera/Tours
   * Arbitrary link support (# and $ in CZML spec)
   * CZML defined user interfaces, possibly with markdown
   * Model support, once Cesium support exists
   * Human readable messages/events raised in CZML
* Widgets & Apps
   * OWF widget
   * Embeddable Cesium Viewer
   * Improved TimeLine widget
   * Standard Cesium toolbar
   * CZML Table of contents/Document Manager widget

## Google Summer of Code Ideas

[Program details](http://code.google.com/soc/).  Most likely due March, 2013.

* Add CZML rendering to Google Maps and/or other popular web mapping APIs
* Particle system
* GML to CZML converter

## ESA Summer of Code in Space Ideas

[Program details](http://sophia.estec.esa.int/socis2012/).  Most likely due June, 2013.

* TODO