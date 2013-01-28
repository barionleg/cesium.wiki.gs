# Roadmap

We're always looking to:
* Write demos that showcase Cesium, especially demos that combine Cesium with other web APIs
* Support more content by writing converters from other formats (GML, [GeoJSON](http://www.geojson.org/), [TopoJSON](https://github.com/mbostock/topojson), [gpx](http://www.topografix.com/gpx.asp) ...) to CZML using our [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer) library
* Write [tutorials](Tutorials-Details) and improve reference documentation and examples
* Improve visual quality and performance - [details](Visual-Quality-and-Performance-Details)
* Improve platform support by fixing issues on various browsers, devices, or video cards
* Improve tests and test coverage; however, we don't blindly chase coverage statistics

## In progress
* Tutorials - [details](Tutorials-Details)
* Streaming terrain - [details](Streaming-Terrain-Details)
* Ocean improvements - [details](Ocean-Details)
* COLLADA models - [details](Models-Details)
* Widget improvements - [details](Widget-Details)
* Playback widget - [details](Playback-Details)
* Space features - [details](Space-features)

## To come

If you are interested in implementing any of these features, start a discussion on the [mailing list](https://groups.google.com/d/forum/cesium-dev).

* Mobile improvements - [details](Mobile-Details)
* Night lights based on streaming imagery that fade out as we zoom in - [data from NASA](http://www.nasa.gov/mission_pages/NPP/news/earth-at-night.html).
* CZML External links - [details](External-links)
* GeoServer CZML writer
* CZML Path/History visualization - [details](CZML-History-visualization-details)
* Screen Space Rendering - [details](Screen-Space-Rendering-Details)
* GLSL #include system - [details](GLSL-Details)
* Draw more shapes - walls, cylinders, boxes, extruded volumes.  Optimize triangulation (faster, less triangles) for circles and ellipses.
* Batching for polygons and potential other shapes.
* Military symbol sets such as MS2525 and NTDS.  SVG files?
* Improve 3D/2D/Columbus view transitions
* Support standard web servers: WMTS, WFS, WCS, ...
* Support for multiple central bodies, i.e., Sun, Moon, etc.
* Build and test server - consider [travis-ci](https://github.com/travis-ci/travis-ci) which integrates with GitHub.
* Shadows
* Video on terrain
* Vectors
* Render buildings
* Label declutter
* Polyline and polygon LOD.  [Douglas-Peucker reduction](http://www.bowdoin.edu/~ltoma/teaching/cs350/spring06/Lecture-Handouts/hershberger92speeding.pdf)
* John Madden-style collaboration among multiple clients
* Particle system
* Volumetric clouds
* Imagery layers improvements - [details](Imagery-Layers-Details)
* Sandcastle improvements - [details](Sandcastle-Details)
* Data-Driven Renderer improvements - [details](Data-Driven-Renderer-Details)
* Material system improvements - [details](Material-System-Details)
* Stars improvements - [details](Stars-Details)
* Website Improvements - [details](Website-Improvement-Details)
* Precision improvements - remove jittering from objects that still do
* Compass - know where north is
* Point clouds - [example data](http://kos.informatik.uni-osnabrueck.de/3Dscans/)
* Run offline
* Do we need built-in video recording?  Consider [ccapture.js](https://github.com/spite/ccapture.js), [sandboxed filesystem](https://gist.github.com/4370822)
* Investigate [Draft for Candidate OpenGIS® Web 3D Service Interface Standard](portal.opengeospatial.org/files/?artifact_id=36390)
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
   * [OWF](https://www.owfgoss.org/) widget
   * Embeddable Cesium Viewer
   * Improved TimeLine widget
   * Standard Cesium toolbar - [details](Cesium-standard-actions)
   * CZML Table of contents/Document Manager widget

## Google Summer of Code Ideas

[Program details](http://code.google.com/soc/).  Most likely due March, 2013.

* Add CZML rendering to Google Maps and/or other popular web mapping APIs
* Particle system
* GML to CZML converter

## Google Code-in

[Program details](http://code.google.com/opensource/gci/2012/index.html)

## ESA Summer of Code in Space Ideas

[Program details](http://sophia.estec.esa.int/socis2012/).  Most likely due June, 2013.

* TODO