## Platforms

### Does Cesium require an install or a plugin?

No.  Cesium runs without an install.  It uses HTML5 standards, namely [WebGL](http://www.khronos.org/webgl/), that are natively supported by browsers.  The only exception is that Internet Explorer requires the [Chrome Frame plugin](http://www.google.com/chromeframe).

### What browsers are supported?

Recent versions of Chrome, Firefox, and Safari are supported.  Internet Explorer is supported by using the [Chrome Frame plugin](http://www.google.com/chromeframe), which is a one-time install that does not require admin rights.  We have not tested on Opera, but expect Cesium to work with some tweaks.

Cesium uses WebGL, and therefore requires a browser that supports WebGL.  There is more support information on the [WebGL wiki](http://www.khronos.org/webgl/wiki/Getting_a_WebGL_Implementation).

The best thing to do is try our [demos](http://cesium.agi.com/) on your target browser.

### What operating systems and devices are supported?

On desktops, Cesium supports Windows, Linux, and Mac.

On mobile, some Android browsers, including Firefox and Opera, support WebGL, but are not ready for prime-time as of June, 2012.  We hope for better WebGL and Cesium support on Android in late 2012 or early 2013.

Although [hacks](http://atnan.com/blog/2011/11/03/enabling-and-using-webgl-on-ios/) exist, iOS only officially supports WebGL for iAds developers so we have not tested Cesium on iOS.  However, we believe that Apple will see the importance of WebGL and the momentum it has, and make it available to all developers.

### What video cards are supported?

Cesium requires a video card that supports WebGL.  Almost all video cards from NVIDIA and AMD since 2004 support WebGL.

To see if your video card supports WebGL, visit our [WebGL Report](http://www.webglreport.com).

### Cesium runs in a browser, but can it also be used to develop a standalone app?

We haven't tried it, but you may be able to use [WebKit](http://www.webkit.org/), [Qt](http://arstechnica.com/business/2012/04/an-in-depth-look-at-qt-5-making-javascript-a-first-class-citizen-for-native-cross-platform-developme/), or [node-webgl](https://github.com/mikeseven/node-webgl) to develop a desktop app using Cesium.  Let us know if you do.

## Formats

### What maps are supported?

WMS, OpenStreetMap, Bing, and Esri.

### What OGC standards are supported?

WMS and a good bit of KML.  We expect WFS later in 2012.  We intend to propose [CZML](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Cesium-Language-%28CZML%29-Guide) as a standard to the OGC when it is battle-tested.

### What vector formats are supported?

CZML, ESRI Shapefiles, WebGL Globe JSON, and a good bit of KML.

## CZML

### Is CZML proprietary?

Absolutely not.  We intend to propose [CZML](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Cesium-Language-%28CZML%29-Guide) as a standard to the OGC when it is battle-tested.

We provide an open source Java and C# [library](https://github.com/AnalyticalGraphicsInc/czml-writer) for writing CZML files, and open source converters to convert from formats like KML and Shapefiles to CZML.  We encourage everyone to write converters to CZML, add CZML rendering support to their engines, and to discuss CZML on our [mailing list](https://groups.google.com/forum/#!forum/cesium-dev).

### How is CZML different than KML?

CZML is able to accurately describe values that change over time, such as the position of a vehicle, using a variety of numerical interpolations.

CZML can be a flat file or can be streamed, such as from real-time telemetry from a vehicle in flight. Clients may join and leave the stream while it is in progress.