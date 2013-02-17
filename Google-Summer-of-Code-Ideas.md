# Google Summer of Code 2013 Idea List

Cesium is an open-source JavaScript library for creating 3D globes and 2D maps in a web browser without a plugin. It uses HTML5 and [WebGL](http://www.khronos.org/webgl) for hardware-accelerated graphics.

**Information for Students**

Cesium developers are eager to work with you.  Our code has shipped to [10's of millions of people in the same day](http://cesium.agi.com/noradtrackssanta2012.html).  We have a culture of writing clean, peer-reviewed, tested code.  We look forward to helping you grow your skills and ship beautiful code that has wide impact.

If you have questions about your proposal, email the project's mentor or discuss it on our [mailing list](https://groups.google.com/forum/#!forum/cesium-dev).  We encourage innovation; we are open to proposals for original projects not listed here.

_Tip:_ Strengthen your proposal by reading our [Contributor's Guide](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Contributor%27s-Guide) and showing that you were able to get Cesium running locally on your machine.  It's easy.  If you need help, [just ask](https://groups.google.com/forum/#!forum/cesium-dev).

## Android Projects

### Android Performance

WebGL support is improving rapidly on Android.  Chrome Beta and Firefox are capable of running Cesium on several phones and tablets.  However, these devices do not have the same CPU and GPU performance as a desktop.  On many devices, Cesium runs well, but that's not enough for us - we want it to scream.

Help us optimize Cesium for these devices.  We will profile to find hot-spots and then tune the GPU code written in GLSL or the CPU code written in JavaScript or both.  We'll consider fundamental architecture changes as needed and will carefully make visual quality vs. speed trade-offs.

Since this is the bleeding edge, we expect to find bugs in the browsers and GPU drivers.  We'll work with browser and GPU vendors to resolve these and make the mobile platform better for everyone.

References
* [Cesium Mobile Compatibility](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Mobile-Details)
* [Fast Mobile Shaders](http://aras-p.info/texts/files/FastMobileShaders_siggraph2011.pdf)

**Skills:** WebGL, JavaScript, Android, profiling, optimizing JavaScript and GLSL, git

**Level:** Advanced

**Mentor:** Kevin?

**Backup Mentor:** Cozzi?

## Graphics

### Declutter for Map Labels

A classic problem in drawing 2D or 3D maps is the overlap of nearby text labels, resulting in a cluttered display and illegible labels.  We will design and implement an efficient real-time algorithm to declutter map labels, avoiding or minimizing overlap.

This is an NP-hard problem, and therefore we will solve it heuristically in an attempt to minimize the amount we move each label and maintain temporal aesthetics.  We will also explore creating hierarchies of labels using [k-means](http://home.dei.polimi.it/matteucc/Clustering/tutorial_html/kmeans.html) and/or knowledge of label relationships, e.g., street - city - county - state.

The algorithm needs to be very efficient; it must run in JavaScript and work for 100s of dynamic labels or 1000s of static labels.

References
* [Temporally Coherent Real-Time Labeling of Dynamic Scenes](http://wwwcg.in.tum.de/research/research/publications/2012/temporally-coherent-real-time-labeling-of-dynamic-scenes.html)
* [K-Means Clutering](http://home.dei.polimi.it/matteucc/Clustering/tutorial_html/kmeans.html)

**Skills:** JavaScript, algorithm design, strong math, code and algorithm optimization, git

**Level:** Advanced

**Mentor:** [Patrick Cozzi](http://www.seas.upenn.edu/~pcozzi/) - pjcozzi@siggraph.org

**Backup Mentor:** TBA

### Compass Rendering

TBA.

**Skills:** WebGL, JavaScript, strong math, git

**Level:** Advanced

**Mentor:** Dan?

**Backup Mentor:** [Patrick Cozzi](http://www.seas.upenn.edu/~pcozzi/) - pjcozzi@siggraph.org

## Geospatial Projects

### Vector Data Visualization with JSON

TBA. [GeoJSON](http://www.geojson.org/) and [TopoJSON](https://github.com/mbostock/topojson)

**Skills:** JavaScript, git, open standards, geospatial

**Level:** Novice

**Mentor:** Amato?

**Backup Mentor:** TBA

### Vector Data Visualization with Geography Markup Language

[Geography Markup Language (GML)](http://www.opengeospatial.org/standards/gml) is an [Open Geospatial Consortium (OGC)](http://www.opengeospatial.org/) standard for expressing geographical features, e.g., points, polylines, and polygons, in XML.

We will add support to Cesium to draw and style features from GML.  The GML spec is quite large with many different feature types.  We can limit our scope to the OpenGIS GML Simple Features Profile, which defines a common subset.

This project is a stepping stone to supporting [Web Feature Service (WFS)](http://www.opengeospatial.org/standards/wfs) below.

References
* [Geography Markup Language (GML)](http://www.opengeospatial.org/standards/gml)

**Skills:** C#, JavaScript, XML, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** TBA

**Backup Mentor:** TBA

### Vector Data Visualization with Web Feature Service

[Web Feature Service (WFS)](http://www.opengeospatial.org/standards/wfs) is an [Open Geospatial Consortium (OGC)](http://www.opengeospatial.org/) standard for requesting geographical features, e.g., points, polylines, and polygons, over the web.

We will add support to Cesium to request geographical features using WFS over HTTP, and draw and style them.  Time permitting, we will also implement client-side creation, deletion, and modification of features and the resulting server updates using WFS-T (Transactional).

This project depends on the [Geography Markup Language (GML)](http://www.opengeospatial.org/standards/gml) project above since WFS features are returned using GML (based on XML).  GML support can be considered a subset of this project or a separate project.

References
* [Web Feature Service](http://www.opengeospatial.org/standards/wfs)

**Skills:** JavaScript, web services, XML, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** TBA

**Backup Mentor:** TBA

### Dynamic Raster Data with Web Map Tile Service

TBA. [Web Map Tile Service (WMTS)](http://www.opengeospatial.org/standards/wmts)

**Skills:** JavaScript, REST APIs, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** TBA

**Backup Mentor:** TBA

## UI

### Navigation Widget

TBA. #450

**Skills:** HTML5, CSS3, SVG, JavaScript, UI design, git

**Level:** Intermediate

**Mentor:** TBA

**Backup Mentor:** TBA

## Misc

### Offline Web App Support

TBA.

References
* [HTML5 Features - Offline](http://www.html5rocks.com/en/features/offline)
* [HTML5 Features - Storage](http://www.html5rocks.com/en/features/storage)
* [Dive Into HTML5: Let's Take This Offline](http://diveintohtml5.info/offline.html)

**Skills:** JavaScript, HTML5, git

**Level:** Novice

**Mentor:** TBA

**Backup Mentor:** TBA