
## Platforms

**Q**: Does Cesium require an install or a plugin?

**A**: No.  Cesium runs without an install.  It uses HTML5 standards, namely WebGL, that are natively supported by web browsers.  The only exception is using Internet Explorer requires the [Chrome Frame plugin](http://www.google.com/chromeframe).

**Q**: What browsers are supported?

**A**: Recent versions of Chrome, Firefox, and Safari are supported.  Internet Explorer is supported by using the [Chrome Frame plugin](http://www.google.com/chromeframe), which is a one-time install that does not require admin rights.  We have not tested on Opera recently, but expect Cesium to work with some tweaks.  Cesium uses [WebGL](http://www.khronos.org/webgl/), and therefore requires a browser that supports WebGL.  There is more support information on the [WebGL wiki](http://www.khronos.org/webgl/wiki/Getting_a_WebGL_Implementation).

The best thing to do is try our [demos](http://cesium.agi.com/) on your target browser.

**Q**: What operating systems and devices are supported?

**A**: On desktops, Cesium supports Windows, Linux, and Mac.

On mobile, some Android browsers, including Firefox and Opera, have WebGL implementations, but we not ready for prime-time as of June, 2012.  We hope for better WebGL and Cesium support on Android in late 2012 or early 2013.

Although [hacks](http://atnan.com/blog/2011/11/03/enabling-and-using-webgl-on-ios/) exist, iOS only officially supports WebGL for iAds developers so we have not tested Cesium on iOS.  However, we believe that Apple will see the importance of WebGL and the momentum it has, and make it available to all developers.

## Standards

**Q**:  What maps are supported?

**A**:  WMS, OpenStreetMap Bing, and Esri.

**Q**:  What OGC standards does Cesium support?

**A**:  WMS and a good bit of KML.  We expect WFS later in 2012.  We intend to propose [CZML](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Cesium-Language-%28CZML%29-Guide) as a standard to the OGC when it is battle-tested.
