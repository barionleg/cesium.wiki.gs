## Supported mobile platforms

As of this writing (October 2012) only two mobile browsers officially support WebGL:
[Firefox](https://play.google.com/store/apps/details?id=org.mozilla.firefox) and
[Opera Mobile](https://play.google.com/store/apps/details?id=com.opera.browser), both
for Android.  Of those, Cesium is not currently able to run on Opera, so Firefox is
the only viable choice.  Not all Android hardware is currently able to run Cesium
on Firefox for Android, some devices show only a black screen, even while other WebGL
demos are able to run.  More debugging is needed.

* ASUS Transformer Prime TF201, Android 4.0.3, tested 03-Oct-2012
   * [Firefox Beta](https://play.google.com/store/apps/details?id=org.mozilla.firefox_beta) works!  So does Aurora and Nightly.
   * Firefox Stable shows a black screen, counts time, correct image only appears in tab thumbnail.
* Motorola Xoom 4G, Android 4.0.4, tested 03-Oct-2012
   * Firefox Beta, Aurora, Nightly show a featureless blue globe with no imagery, doesn't count time.
   * Firefox Stable hangs on black, doesn't count time, likely errors on console (didn't check).
* HTC Evo 4G LTE Sprint, Android 4.0.3, tested 03-Oct-2012
   * Firefox Beta shows a black screen, counts time, nothing appears in tab thumbnail.

## Future potential platforms

We are hoping and expecting both Apple and Google to enable WebGL on their mobile browsers
by default, but there is no known time frame for this.  Apple iOS apparently has hidden
options to [enable WebGL via undocumented calls](http://atnan.com/blog/2011/11/03/enabling-and-using-webgl-on-ios/)
to the WebView interface, that has been discovered and published by
bloggers.  [WebGL Browser](http://benvanik.github.com/WebGLBrowser/) takes
advantage of this to provide a WebGL implementation.

## Supported features

* The CesiumViewerWidget supports single-touch-slide globe rotation
* The TimelineWidget supports single-tap to change time, single-touch-slide to pan (only when zoomed in), and double-touch-slide to zoom.

## Planned features

* CesiumViewerWidget should of course support double-touch-slide to zoom.
* It's been recommended that TimelineWidget should always set the time with single touches, and pan and zoom only with double touches.  This would make it behave more like the desktop version.  Care must be taken to not mistake the first touch of a double-touch for a time-setting event.

## Debugging tools

The primary tool used so far is the Android USB debugging bridge, which displays Firefox console messages on a PC.  Better tools are available:

* [Remote debugging for Firefox](https://hacks.mozilla.org/2012/08/remote-debugging-on-firefox-for-android/)
* [Opera Dragonfly](http://www.opera.com/dragonfly/documentation/) can [remotely connect](http://www.opera.com/dragonfly/documentation/remote/) to Opera Mobile.
* Google Chrome for Android [allows remote debugging](https://developers.google.com/chrome/mobile/docs/debugging)
* [JS Console](http://jsconsole.com/) allows remote execution of JavaScript in almost any browser.

Keep an eye on the [JSD2 branch of Firebug](https://github.com/firebug/firebug/commits/jsd2) which
will enable remote debugging via [Firebug](https://getfirebug.com/).
