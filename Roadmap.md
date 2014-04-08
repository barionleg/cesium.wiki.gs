## In progress

* Camera improvements. [#1060](https://github.com/AnalyticalGraphicsInc/cesium/issues/1060)
* Stabilizing the Cesium API for ease of use, consistency, and an eventual 1.0.  See issues labeled [breaking changes](https://github.com/AnalyticalGraphicsInc/cesium/issues?labels=breaking+change&page=1&state=open).
* 3D model improvements. [#927](https://github.com/AnalyticalGraphicsInc/cesium/issues/927)

Also see issues labeled [roadmap](https://github.com/AnalyticalGraphicsInc/cesium/issues?labels=roadmap&page=1&state=open) and the [Cesium in 2014](https://groups.google.com/forum/#!topic/cesium-dev/cizxRxOEQ8I) forum discussion.

## Ongoing

We're always looking to:
* Write [tutorials](Tutorials-Details) and improve [reference documentation](http://cesiumjs.org/refdoc.html)
* Improve quality by fixing known issues.  If you want to contribute, a good place to start is the [beginner issues](https://github.com/AnalyticalGraphicsInc/cesium/issues?direction=desc&labels=beginner&page=1&sort=updated&state=open)
* Write [demos](http://cesiumjs.org/demos.html) that showcase Cesium, especially demos that combine Cesium with interesting datasets or other web APIs

## Future Ideas

If you are interested in implementing any of these, start a discussion on the [forum](http://cesiumjs.org/forum.html).

* General
  * Client-side KML ([branch](https://github.com/AnalyticalGraphicsInc/cesium/tree/kml)). [#873](https://github.com/AnalyticalGraphicsInc/cesium/issues/873)
  * DynamicScene improvements. [#1045](https://github.com/AnalyticalGraphicsInc/cesium/issues/1045)
  * [Mobile improvements](Mobile-Details)
  * Support more standard web servers: WMTS, WFS, WCS, ...
  * [Sandcastle improvements](Sandcastle-Details)
  * Military symbol sets such as MS2525 and NTDS.  SVG files?
  * Support for multiple central bodies, i.e., Sun, Moon, etc.
* Graphics
  * Terrain and imagery improvements. [#526](https://github.com/AnalyticalGraphicsInc/cesium/issues/526)
  * Label declutter - [#1097](https://github.com/AnalyticalGraphicsInc/cesium/issues/1097) (ESA Summer of Code in Space Project)
  * [Space features](Space-features)
  * [Data-Driven Renderer improvements](Data-Driven-Renderer-Details)
  * [Screen Space Rendering](Screen-Space-Rendering-Details)
  * [Particle system](Particle-System-Details)
  * WebGL extensions - [#797](https://github.com/AnalyticalGraphicsInc/cesium/issues/797)
  * Vectors
  * [Material improvements](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Material-System-Details)
  * Shader pipeline improvements. [#1031](https://github.com/AnalyticalGraphicsInc/cesium/issues/1031)
  * Geometry and appearances improvements. [#766](https://github.com/AnalyticalGraphicsInc/cesium/issues/766)
  * [Stars improvements](Stars-Details)
  * [Ocean improvements](Ocean-Details)
  * Render buildings
  * Video on terrain
  * Point clouds - [data](http://kos.informatik.uni-osnabrueck.de/3Dscans/), [more data](http://opentopo.sdsc.edu/gridsphere/gridsphere?cid=datasets)
  * Volumetric clouds
  * [Visual quality and performance ideas](Visual-Quality-and-Performance-Details)
  * John Madden-style collaboration among multiple clients
  * Polyline and polygon LOD.  [Douglas-Peucker reduction](http://www.bowdoin.edu/~ltoma/teaching/cs350/spring06/Lecture-Handouts/hershberger92speeding.pdf)
  * Lat/lon grid
  * [Lens Flare](http://www.john-chapman.net/content.php?id=18)
  * Investigate [Draft for Candidate OpenGIS® Web 3D Service Interface Standard](portal.opengeospatial.org/files/?artifact_id=36390)
  * Do we need built-in video recording?  Consider [ccapture.js](https://github.com/spite/ccapture.js), [sandboxed filesystem](https://gist.github.com/4370822)
  * Tree generation - Possibly use [this data](http://glcf.umd.edu/data/) to generate global procedural trees.
* CZML
  * [CZML External links](External-links)
  * GeoServer CZML writer
  * [CZML Path/History visualization](CZML-History-visualization-details)
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
  * CZML Table of contents/Document Manager widget
  * Navigation widget - [discussion](https://groups.google.com/forum/#!topic/cesium-dev/TcSLrG0MAnk) and [more discussion](https://groups.google.com/forum/#!topic/cesium-dev/OdhHnshN9fA) (Google Summer of Code Project)
  * Improved TimeLine widget
  * [Standard Cesium toolbar](Cesium-standard-actions)
* Infrastructure
  * [Website Improvements](Website-Improvement-Details)
  * Travis integration. [#652](https://github.com/AnalyticalGraphicsInc/cesium/issues/652)

## Student Programs

* [Google Summer of Code 2014](http://googleblog.blogspot.com/2013/10/50-million-lines-of-code-and-counting.html) - [2013 Ideas](Google-Summer-of-Code-Ideas)
* [ESA Summer of Code in Space 2013 Ideas](ESA-Summer-of-Code-in-Space-Ideas)