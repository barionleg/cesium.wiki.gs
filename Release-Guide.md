We release Cesium on the first work day of every month.  Releases are available on the [downloads page](http://cesium.agi.com/downloads.html).

There is no release manager; instead, our community shares the responsibility.  Any committer can create the release for a given month, and at any point, they can pass the responsibility to someone else, or someone else can ask for it.  This spreads knowledge, avoids stratification, avoids a single point of failure, and is beautifully unstructured.

## Release testing and packaging
1. Verify there are no [show stopper](../issues?labels=show+stopper&page=1&state=open) issues.
1. Send a courtesy message to the [forum](http://cesium.agi.com/forum.html) to let people know you're about to start the release process.
1. Make sure you are using the latest drivers for your video card.
1. Pull down the latest master branch.
1. Update [CHANGES.md](../blob/master/CHANGES.md) with the date of the release.  Also give it a final proof read and tweaking.  Adjust the order of changes so that prominent/popular changes come first.
1. Update [build.xml](../blob/master/build.xml) with the version being released, e.g., `<property name="version" value="b7" />`
1. Commit these changes.
1. Make sure the repository is clean `git clean -d -x -f`. __This will delete all files not already in the repository.__
1. Create the release zips and start the server for testing `./Tools/apache-ant-1.8.2/bin/ant makeZipFile runServer`
1. Verify that the [Documentation](http://localhost:8080/Build/Documentation/index.html) built correctly
1. If running on Windows, each browser should be tested with ANGLE enabled.  The state of ANGLE can be verified using [WebGL Report](http://webglreport.com/).
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) with WebGL validation in [Chrome](https://www.google.com/intl/en/chrome/browser/) stable.
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) with WebGL validation in [Firefox](http://www.mozilla.org/en-US/firefox/new/?from=getfirefox) stable.
1. Make sure [Hello World](http://localhost:8080/Build/HelloWorld.html) loads.
1. Make sure [Cesium Viewer](http://localhost:8080/Apps/CesiumViewer/index.html) loads.
1. Run [Sandcastle](http://localhost:8080/Apps/Sandcastle/index.html) on the browser of your choice (or multiple browsers if you are up for it) and run through each demo to make sure they all work.  Actually play with each of the buttons and sliders on each demo to ensure everything works as expected.
1. If any of the above steps fail, contact the [forum](http://cesium.agi.com/forum.html) to figure out what needs to be fixed before we can release.  Do NOT proceed to the next step until issues are resolved.
1. Create and push a [tag](http://learn.github.com/p/tagging.html), e.g.,
   * `git tag -a b7 -m 'b7 release'`
   * `git push --tags`
1. Branch the [website](http://cesium.agi.com/) and open a pull request for release with post and release zips.  See the [Adding a New Cesium Release](https://github.com/AnalyticalGraphicsInc/cesium-website/wiki/Adding-a-New-Cesium-Release) section of the website wiki.
1. Reply to your courtesy message on the [forum](http://cesium.agi.com/forum.html) to let everyone know the release is ready.

Also, see our [release discussion](https://groups.google.com/forum/#!topic/cesium-dev/ArfdodoROTo) on the forum.