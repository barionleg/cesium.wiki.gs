We release Cesium on the first work day of every month.  Releases are available on the [downloads page](https://github.com/AnalyticalGraphicsInc/cesium/downloads).

There is no release manager; instead, our community shares the responsibility.  Any committer can create the release for a given month, and at any point, they can pass the responsibility to someone else, or someone else can ask for it.  This spreads knowledge, avoids stratification, avoids a single point of failure, and is beautifully unstructured.

## Release testing
1. Make sure you are using the latest drivers for your video card.
1. Make sure you have a clean checkout of `master`.
1. Start the server `./Tools/apache-ant-1.8.2/bin/ant clean build runServer`
1. If running on Windows, each browser should be tested with ANGLE enabled.  The state of ANGLE can be verified using [WebGL Report](http://analyticalgraphicsinc.github.com/webglreport/).
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) in [Chrome](https://www.google.com/intl/en/chrome/browser/) stable.
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) in [Firefox](http://www.mozilla.org/en-US/firefox/new/?from=getfirefox) stable.
1. Run [SandCastle](http://localhost:8080/Apps/Sandcastle/index.html) on the browser of your choice and run through each demo to make sure they all work.
1. Uninstall [Chrome Frame](https://developers.google.com/chrome/chrome-frame/) if you have it installed.
1. Using Internet Explorer, navigate to [Cesium Viewer](http://localhost:8080/Apps/CesiumViewer/index.html) and make sure you are prompted to install Chrome Frame.  There's no need to actually install it.  This step ensures that Cesium fails gracefully on non-WebGL browsers and allows developers to take alternative action.
1. Make sure the documentation builds without errors: `./Tools/apache-ant-1.8.2/bin/ant clean generateDocumentation`
1. If any of the above steps fail, contact the [mailing list](https://groups.google.com/forum/?fromgroups#!forum/cesium-dev) to figure out what needs to be fixed before we can release.  Do NOT release until all steps are passing.

## Packaging for release
1. Update [CHANGES.md](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CHANGES.md) with the date of the release.
1. Update [build.xml](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/build.xml) with the version being released.
1. Create a tag, e.g.,
   * `git tag -a b7 -m 'b7 release'`
   * `git push --tags`
   * For more information on tagging, see [Git Tagging](http://learn.github.com/p/tagging.html).
1. Create a zip file of the build `./Tools/apache-ant-1.8.2/bin/ant clean makeZipFile`
1. Upload the zip to the [downloads page](https://github.com/AnalyticalGraphicsInc/cesium/downloads).
1. Write a [blog](http://cesium.agi.com/blog.html) with a link to [CHANGES.md](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CHANGES.md), highlights for the release, and choice screenshots.

Also, see our [release discussion](https://groups.google.com/forum/#!topic/cesium-dev/ArfdodoROTo) on the mailing list.