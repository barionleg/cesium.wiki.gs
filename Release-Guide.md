We release Cesium on the first work day of every month.  Releases are available on the [downloads page](http://cesiumjs.org/downloads.html).

There is no release manager; instead, our community shares the responsibility.  Any committer can create the release for a given month, and at any point, they can pass the responsibility to someone else, or someone else can ask for it.  This spreads knowledge, avoids stratification, avoids a single point of failure, and is beautifully unstructured ([more info](https://groups.google.com/forum/#!topic/cesium-dev/ArfdodoROTo)).

## Release testing and packaging
1. Verify there are no [show stopper](../issues?labels=show+stopper&page=1&state=open) issues.
1. Verify there are no `remove in [this version number]` [issues](https://github.com/AnalyticalGraphicsInc/cesium/issues).  Rename the label to the next highest `remove in [version]` relative the existing labels.
1. Send a courtesy message to the [forum](http://cesiumjs.org/forum.html) to let people know you're about to start the release process.
1. Make sure you are using the latest drivers for your video card.
1. Pull down the latest master branch.
1. Proofread [CHANGES.md](../blob/master/CHANGES.md) with the date of the release.  Adjust the order of changes so that prominent/popular changes come first.
1. Update [build.xml](../blob/master/build.xml) with the version being released, e.g., `<property name="version" value="b7" />`
1. Commit these changes.
1. Make sure the repository is clean `git clean -d -x -f`. __This will delete all files not already in the repository.__
1. Create the release zips and start the server for testing `./Tools/apache-ant-1.8.2/bin/ant makeZipFile runServer`
1. Verify that the [documentation](http://localhost:8080/Build/Documentation/index.html) built correctly
1. If running on Windows, each browser should be tested with ANGLE enabled.  The state of ANGLE can be verified using [WebGL Report](http://webglreport.com/).
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) with WebGL validation in [Chrome](https://www.google.com/intl/en/chrome/browser/) stable.
1. [Run unit tests](http://localhost:8080/Specs/SpecRunner.html) with WebGL validation in [Firefox](http://www.mozilla.org/en-US/firefox/new/?from=getfirefox) stable.
1. Make sure [Hello World](http://localhost:8080/Build/HelloWorld.html) loads.
1. Make sure [Cesium Viewer](http://localhost:8080/Apps/CesiumViewer/index.html) loads.
1. Run [Sandcastle](http://localhost:8080/Apps/Sandcastle/index.html) on the browser of your choice (or multiple browsers if you are up for it) and run through each demo to make sure they all work.  Actually play with each of the buttons and sliders on each demo to ensure everything works as expected.
1. If any of the above steps fail, contact the [forum](http://cesiumjs.org/forum.html) to figure out what needs to be fixed before we can release.  Do NOT proceed to the next step until issues are resolved.
1. Create and push a [tag](http://learn.github.com/p/tagging.html), e.g.,
   * `git tag -a b7 -m 'b7 release'`
   * `git push origin b7` (this assumes origin is the primary cesium repository, do not use `git push --tags` as it pushes all tags from all remotes you have on your system.)
1. [Add the release to cesiumjs.org](https://github.com/AnalyticalGraphicsInc/cesium-website/wiki/Adding-a-New-Cesium-Release).
1. Reply to your courtesy message on the [forum](http://cesiumjs.org/forum.html) to let everyone know the release is ready.
1. Announce the release on twitter using [@CesiumJS](https://twitter.com/CesiumJS) with a link to the blog post.