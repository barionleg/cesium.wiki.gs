# Google Summer of Code 2013 Idea List

<p align="center">
<img src="gsoc/2013/cesium1.png">
<img src="gsoc/2013/cesium2.png">
</p>

[Cesium](http://cesium.agi.com/) is an open-source JavaScript library for creating 3D globes and 2D maps in a web browser without a plugin. It uses HTML5 and [WebGL](http://www.khronos.org/webgl) for hardware-accelerated graphics.

**Information for Students**

Cesium developers are eager to work with you.  Our code has shipped to [10's of millions of people in the same day](http://cesium.agi.com/noradtrackssanta2012.html).  We have a culture of writing clean, peer-reviewed, tested code.  Our developers are experts in their fields; they write books, create open standards, and present at international conferences.  We look forward to helping you grow your skills and ship beautiful code that has wide impact.

If you have questions about your proposal, email the project's mentor or discuss it on our [mailing list](https://groups.google.com/forum/#!forum/cesium-dev).  We encourage innovation; we are open to proposals for original projects not listed below.  See our [roadmap](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Roadmap) for ideas.

_Tip:_ Strengthen your proposal by reading our [Contributor's Guide](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Contributor%27s-Guide) and showing that you were able to get Cesium running locally on your machine.  It's easy.  If you need help, [just ask](https://groups.google.com/forum/#!forum/cesium-dev).  Make your proposal even stronger by tackling an issue or two, see our [list of issues for beginners](https://github.com/AnalyticalGraphicsInc/cesium/issues?labels=GSoC&state=open).

## Submitting Proposals

<p align="center">
<a href="http://google-melange.appspot.com/gsoc/org/google/gsoc2013/cesium"><img src="gsoc/2013/banner-gsoc2013.png"></a>
</p>

Student proposals are submitted through [Cesium's page on the Google Summer of Code website](http://google-melange.appspot.com/gsoc/org/google/gsoc2013/cesium).

Proposals are being accepted from April 22, 19:00 UTC through May 3rd 2013, 19:00 UTC.  (see the [full schedule](http://google-melange.appspot.com/gsoc/events/google/gsoc2013).)

**Get your feet wet**

It can be quite helpful to learn about our codebase and try making some simple modifications to it, prior to submitting your proposal.  Check out our issues flagged with [the GSoC label](https://github.com/AnalyticalGraphicsInc/cesium/issues?labels=GSoC&state=open) to see if there are any that might make a good first bugfix for you.

All of Cesium's code is covered by a Contributor's License Agreement (CLA), which basically authorizes Cesium developers and users to use the code you're contributing to us.  You'll need to read the instructions for [contributing to Cesium](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CONTRIBUTING.md) and email us a signed CLA before we can accept any code changes.

**Technologies and Tools We Use**

(We don't expect you to know all of them).

HTML5, CSS3, JavaScript, WebGL, SVG, Git, Ant, Eclipse, Chrome, Firefox, Android

**Project Ideas**
* [Android](#android)
   * [Android Performance](#androidperformance)
* [Graphics](#graphics)
   * [Declutter for Map Labels](#decultterformaplabels)
   * [Geometric Algorithms](#geometricalgorithms)
* [Geospatial](#geospatial)
   * [Vector Data Visualization with JSON](#json)
   * [Raster Data Visualization with Web Map Tile Service](#wmts)
   * [Vector Data Visualization with Geography Markup Language](#gml)
   * [Vector Data Visualization with Web Feature Service](#wfs)
* [UI](#ui)
   * [Navigation Widget](#navigationwidget)
   * [Credits Layout](#creditslayout)
* [Misc](#misc)
   * [Offline Web App Support](#offlinewebappsupport)

<a name="android">
# Android

<a name="androidperformance">
## Android Performance

WebGL support is improving rapidly on Android.  Chrome, Firefox, and Opera Beta are capable of running Cesium on several phones and tablets.  However, these devices do not have the same CPU and GPU performance as a desktop.  On many devices, Cesium runs well, but that's not enough for us - we want it to scream.

Help us optimize Cesium for these devices.  We will profile to find hot-spots and then tune the GPU code written in GLSL or the CPU code written in JavaScript or both.  We'll consider fundamental architecture changes as needed and will carefully make visual quality vs. speed trade-offs.

Since this is the bleeding edge, we expect to find bugs in the browsers and GPU drivers.  We'll work with browser and GPU vendors to resolve these and make the mobile platform better for everyone.

References
* [Cesium Mobile Compatibility](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Mobile-Details)
* [Fast Mobile Shaders](http://aras-p.info/texts/files/FastMobileShaders_siggraph2011.pdf)

**Skills:** WebGL, JavaScript, Android, profiling, optimizing JavaScript and GLSL, git

**Level:** Advanced

**Mentor:** [Kevin Ring](http://www.kotachrome.com/kevin) - kevin@kotachrome.com

**Backup Mentor:** [Patrick Cozzi](http://www.seas.upenn.edu/~pcozzi/) - pjcozzi@siggraph.org

<a name="graphics">
# Graphics

<a name="decultterformaplabels">
## Declutter for Map Labels

![](gsoc/2013/declutter.png)
<br /><small>Image from [Temporally Coherent Real-Time Labeling of Dynamic Scenes](http://wwwcg.in.tum.de/research/research/publications/2012/temporally-coherent-real-time-labeling-of-dynamic-scenes.html)</small>

A classic problem when drawing 2D or 3D maps is the overlap of nearby text labels, resulting in a cluttered display and illegible labels.  We will design and implement an efficient real-time algorithm to declutter map labels, avoiding or minimizing overlap.

This is an NP-hard problem, and therefore we will solve it heuristically in an attempt to minimize the amount we move each label and maintain temporal aesthetics.  We will also explore creating hierarchies of labels using [k-means](http://home.dei.polimi.it/matteucc/Clustering/tutorial_html/kmeans.html) and/or knowledge of hierarchical label relationships, e.g., street - city - county - state.

The algorithm needs to be very efficient; it must run in JavaScript and work for 100s of dynamic labels or 1000s of static labels.

References
* [Temporally Coherent Real-Time Labeling of Dynamic Scenes](http://wwwcg.in.tum.de/research/research/publications/2012/temporally-coherent-real-time-labeling-of-dynamic-scenes.html)
* [Dynamic Label Placement for Improved Interactive Exploration](http://maverick.inria.fr/Publications/2008/SD08/index.php)
* [K-Means Clustering](http://home.dei.polimi.it/matteucc/Clustering/tutorial_html/kmeans.html)

**Skills:** Algorithm design, strong math, code and algorithm optimization, JavaScript, git

**Level:** Advanced

**Mentor:** [Patrick Cozzi](http://www.seas.upenn.edu/~pcozzi/) - pjcozzi@siggraph.org

**Backup Mentor:** [Dan Bagnell](https://github.com/bagnell) - dbagnell@agi.com

<a name="geometricalgorithms">
## Geometric Algorithms

![](gsoc/2013/geometricalgorithms.png)

We use geometric algorithms to compute triangles composing shapes on the globe such as circles, ellipsoids, polygons, etc.  We then use the triangles to draw the shape using WebGL.

In this project, we will add geometric algorithms for new shapes and optimize existing geometric algorithms.  We will:
   * Add triangulation for walls perpendicular to the globe.  This includes computing positions, averaged normals, and texture coordinates.
   * Add triangulation for "ribbon lines" - think the geometry for the track in [Rainbow Road](http://i1.sndcdn.com/artworks-000010122970-0spcry-original.png?daca7bd).
   * Add triangulation for hexahedrons.
   * Optimize polygon ear clipping and improve its robustness at the International Date Line.
   * Optimize triangulation for circles and ellipses.

We'll consider other shapes and level of detail as time permits.

References
* [Triangulation by Ear Clipping](http://www.geometrictools.com/Documentation/TriangulationByEarClipping.pdf)

**Skills:** Strong geometry and math skills, data structures and algorithms, optimization, JavaScript, git

**Level:** Intermediate

**Mentor:** [Dan Bagnell](https://github.com/bagnell) - dbagnell@agi.com

**Backup Mentor:** [Patrick Cozzi](http://www.seas.upenn.edu/~pcozzi/) - pjcozzi@siggraph.org

<a name="geospatial">
# Geospatial

<a name="json">
## Vector Data Visualization with JSON

![](gsoc/2013/json.png)

KML is a popular XML-based format for storing vector data, i.e., points, polylines, and polygons.  However, new JSON-based standards are emerging that are better suited to web mapping.

In this project, we will add support for two JSON vector data formats, [GeoJSON](http://www.geojson.org/) and [TopoJSON](https://github.com/mbostock/topojson), to Cesium.  First, we'll load and draw them using the Cesium API.  Then we'll investigating styling with colors, patterns, etc.

References
* [The GeoJSON Format Specification](http://www.geojson.org/geojson-spec.html)
* [GeoJSONLint](http://geojsonlint.com/)
* [TopoJSON Specification](https://github.com/mbostock/topojson/wiki/Specification)

**Skills:** JavaScript, git, open standards, geospatial

**Level:** Novice

**Mentor:** [Matt Amato](https://twitter.com/matt_amato) - mamato@agi.com

**Backup Mentor:** Ford?

<a name="wmts">
## Raster Data Visualization with Web Map Tile Service

![](gsoc/2013/wmts.png)

Cesium draws 3D maps retrieved using many map standards like [Web Map Service (WMS)](http://www.opengeospatial.org/standards/wms) and [OpenStreetMap](http://wiki.openstreetmap.org/wiki/Main_Page).  These standards provide access to high-resolution maps.

In this project, we will add support for [Web Map Tile Service (WMTS)](http://www.opengeospatial.org/standards/wmts), an [Open Geospatial Consortium (OGC)](http://www.opengeospatial.org/) standard.  WMTS allows serving static tiles as individual files, and generally performs better than WMS.

References
* [Web Map Tile Service (WMTS)](http://www.opengeospatial.org/standards/wmts)
* [Cesium Imagery Layers Tutorial](http://cesium.agi.com/2013/01/04/Cesium-Imagery-Layers-Tutorial/)

**Skills:** JavaScript, REST APIs, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** [Tom Fili](https://github.com/tfili) - tfili@agi.com

**Backup Mentor:** [Kevin Ring](http://www.kotachrome.com/kevin) - kevin@kotachrome.com

<a name="gml">
## Vector Data Visualization with Geography Markup Language

![](gsoc/2013/gml.png)

[Geography Markup Language (GML)](http://www.opengeospatial.org/standards/gml) is an [Open Geospatial Consortium (OGC)](http://www.opengeospatial.org/) standard for expressing geographical features, e.g., points, polylines, and polygons, in XML.

In this project, we will add support to Cesium to draw and style features from GML.  The GML spec is quite large with many different feature types.  We can limit our scope to the OpenGIS GML Simple Features Profile, which defines a common subset.

This project is a stepping stone to supporting [Web Feature Service (WFS)](http://www.opengeospatial.org/standards/wfs) below.

References
* [Geography Markup Language (GML)](http://www.opengeospatial.org/standards/gml)

**Skills:** JavaScript, XML, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** TBA

**Backup Mentor:** TBA

<a name="wfs">
## Vector Data Visualization with Web Feature Service

![](gsoc/2013/wfs.png)

[Web Feature Service (WFS)](http://www.opengeospatial.org/standards/wfs) is an [Open Geospatial Consortium (OGC)](http://www.opengeospatial.org/) standard for requesting geographical features, e.g., points, polylines, and polygons, over the web.

In this project, we will add support to Cesium to request geographical features using WFS over HTTP, and draw and style them.  Time permitting, we will also implement client-side creation, deletion, and modification of features and the resulting server updates using WFS-T (Transactional).

This project depends on the [Geography Markup Language (GML)](http://www.opengeospatial.org/standards/gml) project above since WFS features are returned using GML (based on XML).  GML support can be considered a subset of this project or a separate project.

References
* [Web Feature Service](http://www.opengeospatial.org/standards/wfs)

**Skills:** JavaScript, web services, XML, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** TBA

**Backup Mentor:** TBA

<a name="ui">
# UI

<a name="navigationwidget">
## Navigation Widget

![](gsoc/2013/navigationwidget.png)

Cesium provides default mouse and touch input for the camera, including:
* Left click and drag - Rotates the camera around the globe in 3D and translates the camera over the map surface in 2D and Columbus view.
* Right click and drag - Zooms the camera in and out.
* Middle wheel scrolling - Also zooms the camera in and out.
* Middle click and drag - Rotates the camera around the point on the surface of the globe.

In this project, we'll create a modern widget, potentially using SVG, to allow the user to perform these camera actions with just the left mouse button or single click.  We'll also consider adding an instruction overlays demonstrating mouse and touch controls.  More ideas for this project [here](https://github.com/AnalyticalGraphicsInc/cesium/issues/450).

![](gsoc/2013/nav-concept.png)

The nav widget would likely include some sort of a compass, which might or might not look anything like the above.

References
* [Cesium Camera Tutorial](http://cesium.agi.com/2013/02/13/Cesium-Camera-Tutorial/)

**Skills:** Eye for aesthetic UI design, HTML5, CSS3, SVG, JavaScript, git

**Level:** Intermediate

**Mentor:** [Ed Mackey](https://twitter.com/emackey) - ed-cesium@snappymaria.com

**Backup Mentor:** [Matt Amato](https://twitter.com/matt_amato) - mamato@agi.com

<a name="creditslayout">
## Credits Layout

![](gsoc/2013/creditslayout.png)

Cesium draws content (terrain, imagery, models, etc.) from external sources that need to be credited when their content is visible as shown in the screenshot above.  Depending on what content is loaded or visible, the displayed credit (image or text) can vary.

In this project, we'll design an API to mange credits and aesthetically overlay them on the 3D scene.

**Skills:** Eye for aesthetic UI design, JavaScript, git

**Level:** Novice

**Mentor:** [Scott Hunter](https://github.com/shunter) - scott.k.hunter@gmail.com

**Backup Mentor:** [Ed Mackey](https://twitter.com/emackey) - ed-cesium@snappymaria.com

<a name="misc">
# Misc

<a name="offlinewebappsupport">
## Offline Web App Support

![](gsoc/2013/offline.png)

Cesium provides a realistic virtual globe by streaming high-resolution terrain and imagery on-demand.  However, users without a network connection or an unreliable network connection cannot rely on the connection to servers hosting terrain, imagery, and other data used by Cesium.

In this project, we'll use new HTML5 features to design and implement offline support in Cesium.  That is, we'll let users select and download data for an area of the globe (pending the data provider's terms of use) so that users can use Cesium later without connectivity.

References
* [HTML5 Features - Offline](http://www.html5rocks.com/en/features/offline)
* [HTML5 Features - Storage](http://www.html5rocks.com/en/features/storage)
* [Dive Into HTML5: Let's Take This Offline](http://diveintohtml5.info/offline.html)

**Skills:** JavaScript, HTML5, git

**Level:** Novice

**Mentor:** [Scott Hunter](https://github.com/shunter) - scott.k.hunter@gmail.com

**Backup Mentor:** [Kevin Ring](http://www.kotachrome.com/kevin) - kevin@kotachrome.com

<hr />
<p align="center">
<a href="http://www.google-melange.com/gsoc/org/google/gsoc2013/cesium" target="_blank">Main Google Summer of Code Page for Cesium</a>
</p>