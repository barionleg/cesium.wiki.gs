# Roadmap

We're always looking to:
* Write demos that showcase Cesium, especially demos that combine Cesium with other web APIs
* Support more content by writing converters from other formats (GML, [GeoJSON](http://www.geojson.org/), [TopoJSON](https://github.com/mbostock/topojson), [gpx](http://www.topografix.com/gpx.asp) ...) to CZML using our [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer) library
* Write [tutorials](Tutorials-Details) and improve reference documentation and examples
* Improve platform support by fixing issues on various browsers, devices, or video cards
* Improve tests and test coverage

## In progress
* Client-side KML - [#873](https://github.com/AnalyticalGraphicsInc/cesium/issues/873)
* Navigation Widget - [discussion](https://groups.google.com/forum/#!topic/cesium-dev/TcSLrG0MAnk) and [more discussion](https://groups.google.com/forum/#!topic/cesium-dev/OdhHnshN9fA)
* New geometry types and batching - [#766](https://github.com/AnalyticalGraphicsInc/cesium/issues/766)
* 3D models - [details](Models-Details)
* Space features - [details](Space-features)
* Screen Space Rendering - [details](Screen-Space-Rendering-Details)
* Tutorials - [details](Tutorials-Details)

Also see the [Cesium in 2013](https://groups.google.com/forum/#!topic/cesium-dev/roG1XTqbcUk) discussion.

## To come

If you are interested in implementing any of these features, start a discussion on the [forum](http://cesium.agi.com/forum.html).

* General
   * [ESA Summer of Code in Space Ideas](ESA-Summer-of-Code-in-Space-Ideas)
   * Mobile improvements - [details](Mobile-Details)
   * Support standard web servers: WMTS, WFS, WCS, ...
   * Support for multiple central bodies, i.e., Sun, Moon, etc.
   * Sandcastle improvements - [details](Sandcastle-Details)
   * Military symbol sets such as MS2525 and NTDS.  SVG files?
* Graphics
   * Night lights based on streaming imagery that fade out as we zoom in - [data from NASA](http://www.nasa.gov/mission_pages/NPP/news/earth-at-night.html).
   * Improve 3D/2D/Columbus view transitions
   * GLSL #include system - [details](GLSL-Details)
   * Particle system - [details](Particle-System-Details)
   * Data-Driven Renderer improvements - [details](Data-Driven-Renderer-Details)
   * WebGL extensions - [#797](https://github.com/AnalyticalGraphicsInc/cesium/issues/797)
   * Vectors
   * Polyline and polygon LOD.  [Douglas-Peucker reduction](http://www.bowdoin.edu/~ltoma/teaching/cs350/spring06/Lecture-Handouts/hershberger92speeding.pdf)
   * Lat/lon grid
   * John Madden-style collaboration among multiple clients
   * Terrain and imagery improvements - [#526](https://github.com/AnalyticalGraphicsInc/cesium/issues/526)
   * Stars improvements - [details](Stars-Details)
   * Ocean improvements - [details](Ocean-Details)
   * Render buildings
   * Video on terrain
   * Investigate [Draft for Candidate OpenGIS® Web 3D Service Interface Standard](portal.opengeospatial.org/files/?artifact_id=36390)
   * Point clouds - [example data](http://kos.informatik.uni-osnabrueck.de/3Dscans/)
   * Do we need built-in video recording?  Consider [ccapture.js](https://github.com/spite/ccapture.js), [sandboxed filesystem](https://gist.github.com/4370822)
   * Volumetric clouds
   * [Lens Flare](http://www.john-chapman.net/content.php?id=18)
   * Visual quality and performance ideas - [details](Visual-Quality-and-Performance-Details)
   * Tree generation - Possibly use [this data](http://glcf.umd.edu/data/) to generate global procedural trees.
* CZML
   * CZML External links - [details](External-links)
   * GeoServer CZML writer
   * CZML Path/History visualization - [details](CZML-History-visualization-details)
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
* Infrastructure
   * Website Improvements - [details](Website-Improvement-Details)
   * Travis integration - [#652](https://github.com/AnalyticalGraphicsInc/cesium/issues/652)

## Google Summer of Code 2013

* [Google Summer of Code Ideas](Google-Summer-of-Code-Ideas)

## Google Code-in

[Program details](http://code.google.com/opensource/gci/2012/index.html)

## ESA Summer of Code in Space Ideas

[Program details](http://sophia.estec.esa.int/socis2012/).  Most likely due June, 2013.