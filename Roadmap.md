## In progress

* See the [Cesium in 2015](https://groups.google.com/forum/#!topic/cesium-dev/Z_RE-krc0HY) forum discussion.
* KML ([branch](https://github.com/AnalyticalGraphicsInc/cesium/compare/kml...dataSourceBrowser)). [#873](https://github.com/AnalyticalGraphicsInc/cesium/issues/873), [#2179](https://github.com/AnalyticalGraphicsInc/cesium/issues/2179)
* Polygons, polylines, billboards, and labels clamped to terrain. [#2172](https://github.com/AnalyticalGraphicsInc/cesium/issues/2172)
* [Google Summer of Code 2015](Google-Summer-of-Code-Ideas-2015)

## Ongoing

We're always looking to:
* Write [tutorials](Tutorials-Details) and improve [reference documentation](http://cesiumjs.org/refdoc.html)
* Improve quality by fixing known issues.  If you want to contribute, a good place to start is the [beginner issues](https://github.com/AnalyticalGraphicsInc/cesium/issues?direction=desc&labels=beginner&page=1&sort=updated&state=open)
* Write [demos](http://cesiumjs.org/demos.html) that showcase Cesium, especially demos that combine Cesium with interesting datasets or other web APIs

## Future Ideas (some have progress already)

If you are interested in implementing any of these, start a discussion on the [forum](http://cesiumjs.org/forum.html).

* See issues labeled [roadmap](https://github.com/AnalyticalGraphicsInc/cesium/issues?q=is%3Aopen+is%3Aissue+label%3Aroadmap)
* General
  * DataSource improvements. [#1045](https://github.com/AnalyticalGraphicsInc/cesium/issues/1045)
  * [Mobile improvements](Mobile-Details)
  * [Sandcastle improvements](Sandcastle-Details)
  * More standard web services: WFS, WCS, ...
  * Military symbol sets such as MS2525 and NTDS.  SVG files?
  * Support for multiple central bodies, i.e., Sun, Moon, etc.
* Graphics
  * Geometry and appearances improvements. [#766](https://github.com/AnalyticalGraphicsInc/cesium/issues/766)
  * 3D model improvements. [#927](https://github.com/AnalyticalGraphicsInc/cesium/issues/927)
  * Dynamic buffers. [#932](https://github.com/AnalyticalGraphicsInc/cesium/issues/932)
  * Line styles. [paper](http://jcgt.org/published/0002/02/08/)
  * Terrain and imagery improvements. [#526](https://github.com/AnalyticalGraphicsInc/cesium/issues/526)
  * Shadows (part of [Data-Driven Renderer](Data-Driven-Renderer-Details))
  * [Post-Processing Framework](Screen-Space-Rendering-Details) ([branch](https://github.com/AnalyticalGraphicsInc/cesium/compare/master...postprocess-hook))
  * [Particle system](Particle-System-Details)
  * Label declutter. [#1097](https://github.com/AnalyticalGraphicsInc/cesium/issues/1097)
  * [Space features](Space-features)
  * Refactor internal Columbus View architecture.
  * WebGL extensions. [#797](https://github.com/AnalyticalGraphicsInc/cesium/issues/797)
  * Content
     * Buildings
     * Point clouds. [data](http://kos.informatik.uni-osnabrueck.de/3Dscans/), [more data](http://opentopo.sdsc.edu/gridsphere/gridsphere?cid=datasets), [even more data](https://lta.cr.usgs.gov/LIDAR)
     * Trees - Possibly use [this data](http://glcf.umd.edu/data/) to generate global procedural. [Cambridge data](https://www.cambridgema.gov/theworks/ourservices/urbanforestry/treeinventory.aspx) and [OpenTreeMap](https://www.opentreemap.org/).
     * Volumetric clouds
     * [Stars improvements](Stars-Details)
  * [Ocean improvements](Ocean-Details)
  * Video on terrain
  * John Madden-style collaboration among multiple clients
  * Polyline and polygon LOD.  [Douglas-Peucker reduction](http://www.bowdoin.edu/~ltoma/teaching/cs350/spring06/Lecture-Handouts/hershberger92speeding.pdf)
  * Lat/lon grid
  * Shader pipeline improvements. [#1031](https://github.com/AnalyticalGraphicsInc/cesium/issues/1031)
  * [Material improvements](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Material-System-Details)
  * Investigate [Draft for Candidate OpenGIS® Web 3D Service Interface Standard](portal.opengeospatial.org/files/?artifact_id=36390)
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
* Widgets
   * Data Source Browser widget ([branch](https://github.com/AnalyticalGraphicsInc/cesium/compare/master...dataSourceBrowser))
  * Navigation widget. [#450](https://github.com/AnalyticalGraphicsInc/cesium/issues/450)
  * Improved TimeLine widget
  * [Standard Cesium toolbar](Cesium-standard-actions)

## Past Student Programs

* [Google Summer of Code 2013](Google-Summer-of-Code-Ideas)
* [ESA Summer of Code in Space 2013 Ideas](ESA-Summer-of-Code-in-Space-Ideas)