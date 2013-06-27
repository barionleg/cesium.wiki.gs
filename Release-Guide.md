We release Cesium on the first work day of every month.  Releases are available on the [downloads page](http://cesium.agi.com/downloads.html).

There is no release manager; instead, our community shares the responsibility.  Any committer can create the release for a given month, and at any point, they can pass the responsibility to someone else, or someone else can ask for it.  This spreads knowledge, avoids stratification, avoids a single point of failure, and is beautifully unstructured.

## Release testing
1. Verify there are no [show stopper](../issues?labels=show+stopper&page=1&state=open) issues.
1. Send a courtesy message to the [forum](http://cesium.agi.com/forum.html) to let people know you're about to start the release process.
1. Make sure you are using the latest drivers for your video card.
1. Make sure you have a clean checkout of `master`.
1. Make sure Cesium and its documentation builds without errors: `./Tools/apache-ant-1.8.2/bin/ant clean combine generateDocumentation`
1. Start the server `./Tools/apache-ant-1.8.2/bin/ant runServer`
1. If running on Windows, each browser should be tested with ANGLE enabled.  The state of ANGLE can be verified using [WebGL Report](http://analyticalgraphicsinc.github.com/webglreport/).
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) in [Chrome](https://www.google.com/intl/en/chrome/browser/) stable.
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) in [Firefox](http://www.mozilla.org/en-US/firefox/new/?from=getfirefox) stable.
1. Run JSHint on the source code by running `./Tools/apache-ant-1.8.2/bin/ant jsHint`.
1. Run [Sandcastle](http://localhost:8080/Apps/Sandcastle/index.html) on the browser of your choice and run through each demo to make sure they all work.
1. Uninstall [Chrome Frame](https://developers.google.com/chrome/chrome-frame/) if you have it installed.
1. Using Internet Explorer, navigate to [Cesium Viewer](http://localhost:8080/Apps/CesiumViewer/index.html) and make sure you are prompted to install Chrome Frame.  There's no need to actually install it.  This step ensures that Cesium fails gracefully on non-WebGL browsers and allows developers to take alternative action.
1. If any of the above steps fail, contact the [forum](http://cesium.agi.com/forum.html) to figure out what needs to be fixed before we can release.  Do NOT release until all steps are passing.

## Packaging for release
1. Update [CHANGES.md](../blob/master/CHANGES.md) with the date of the release.
1. Update [build.xml](../blob/master/build.xml) with the version being released, e.g., `<property name="version" value="b7" />`
1. Commit these changes.
1. Make sure the repository is clean `git clean -d -x -f`. __This will delete all files not already in the repository.__
1. Create a zip file of the build `./Tools/apache-ant-1.8.2/bin/ant makeZipFile`
1. Create and push a [tag](http://learn.github.com/p/tagging.html), e.g.,
   * `git tag -a b7 -m 'b7 release'`
   * `git push --tags`
1. Deploy to the [website](http://cesium.agi.com/).  See the _Adding a New Cesium Release_ section of the website wiki.
1. Reply to your courtesy message on the [forum](http://cesium.agi.com/forum.html) to let everyone know the release is ready.

Also, see our [release discussion](https://groups.google.com/forum/#!topic/cesium-dev/ArfdodoROTo) on the forum.