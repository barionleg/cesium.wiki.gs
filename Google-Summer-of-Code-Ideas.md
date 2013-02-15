# Google Summer of Code 2013 Idea List

Cesium is a JavaScript library for creating 3D globes and 2D maps in a web browser without a plugin. It uses HTML5 and [WebGL](http://www.khronos.org/webgl) for hardware-accelerated graphics.

**Information for Students**

Cesium developers are eager to work with you.  Our code has shipped to [10's of millions of people in the same day](http://cesium.agi.com/noradtrackssanta2012.html).  We have a culture of writing clean, peer-reviewed, tested code.  We look forward to helping you grow your skills and ship beautiful code that has wide impact.

If you have questions about your proposal, email the project's mentor or discuss it on our [mailing list](https://groups.google.com/forum/#!forum/cesium-dev).  We encourage innovation; we are open to proposals for original projects not listed here.

## Mobile Projects

### Mobile Performance

[WebGL](http://www.khronos.org/webgl/) support is improving rapidly on Android.  Chrome Beta and Firefox are capable of running Cesium on several phones and tablets.  However, these devices do not have the same CPU and GPU performance as a desktop.  On many devices, Cesium runs well, but that's not enough for us - we want it to scream.

Help us optimize Cesium for these devices.  We will profile to find hot-spots and then tune the GPU code written in GLSL or the CPU code written in JavaScript or both.  We'll consider fundamental architecture changes as needed and will carefully make visual quality vs. speed trade-offs.

Since this is the bleeding edge, we expect to find bugs in the browsers and GPU drivers.  We'll work with browser and GPU vendors to resolve these and make the mobile platform better for everyone.

References
* [Cesium Mobile Compatibility](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Mobile-Details)
* [Fast Mobile Shaders](http://aras-p.info/texts/files/FastMobileShaders_siggraph2011.pdf)

**Skills:** WebGL, JavaScript, Android, profiling, low-level optimizations for JavaScript and GLSL, git

**Level:** Advanced

**Mentor:** Kevin?

## Graphics

### Declutter for Map Labels

TBA.

**Skills:** JavaScript, NP-hard algorithm design, git

**Level:** Advanced

**Mentor:** [Patrick Cozzi](http://www.seas.upenn.edu/~pcozzi/) - pjcozzi@siggraph.org

### Compass Rendering

TBA.

**Skills:** WebGL, JavaScript, strong math, git

**Level:** Advanced

**Mentor:** Dan?

## Geospatial Projects

### Vector Data Visualization with JSON

TBA. [GeoJSON](http://www.geojson.org/) and [TopoJSON](https://github.com/mbostock/topojson)

**Skills:** JavaScript, git, open standards, geospatial

**Level:** Novice

**Mentor:** Amato?

### Vector Data Visualization with the Web Feature Service

TBA. [Web Feature Service (WFS)](http://www.opengeospatial.org/standards/wfs)

**Skills:** JavaScript, REST APIs, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** Cozzi?

### Vector Data Visualization with the Geography Markup Language

TBA. [Geography Markup Language (GML)](http://www.opengeospatial.org/standards/gml)

**Skills:** C#, JavaScript, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** TBA

### Dynamic Raster Data with the Web Map Tile Service

TBA. [Web Map Tile Service (WMTS)](http://www.opengeospatial.org/standards/wmts)

**Skills:** JavaScript, REST APIs, git, open standards, geospatial

**Level:** Intermediate

**Mentor:** TBA

## UI

### Navigation Widget

TBA. #450

**Skills:** HTML5, CSS3, SVG, JavaScript, UI design, git

**Level:** Intermediate

**Mentor:** TBA

## Misc

### Offline Web App Support

TBA.

**Skills:** JavaScript, HTML5, git

**Level:** Novice

**Mentor:** TBA