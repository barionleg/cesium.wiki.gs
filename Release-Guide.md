We release Cesium on the first work day of every month.  Releases are available on the [downloads page](https://github.com/AnalyticalGraphicsInc/cesium/downloads).

There is no release manager; instead, our community shares the responsibility.  Any committer can create the release for a given month, and at any point, they can pass the responsibility to someone else, or someone else can ask for it.  This spreads knowledge, avoids stratification, avoids a single point of failure, and is beautifully unstructured.

Create a release using master:
* Update [CHANGES.md](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CHANGES.md) with the date of the release.
* Update [build.xml](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/build.xml) with the version being released.
* Create a tag, e.g.,
   * `git tag -a b7 -m 'b7 release'`
   * `git push --tags`
   * For more information on tagging, see [Git Tagging](http://learn.github.com/p/tagging.html).
* Create a zip file of the build.
   * `./Tools/apache-ant-1.8.2/bin/ant clean`
   * `./Tools/apache-ant-1.8.2/bin/ant makeZipFile`
* Upload the zip to the [downloads page](https://github.com/AnalyticalGraphicsInc/cesium/downloads).
* Email the [announcement mailing list](https://groups.google.com/forum/#!forum/cesium-announce) with a link to [CHANGES.md](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CHANGES.md) and highlights for the release.

Also, see our [release discussion](https://groups.google.com/forum/#!topic/cesium-dev/ArfdodoROTo) on the mailing list.