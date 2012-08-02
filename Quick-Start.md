Getting started with a local copy of Cesium on Windows, Linux, and Mac is quick.

## Get the Code

* `git clone git@github.com:AnalyticalGraphicsInc/cesium.git`
   * Or download the [zip of master](https://github.com/AnalyticalGraphicsInc/cesium/zipball/master).
   * Or visit the [downloads page](https://github.com/AnalyticalGraphicsInc/cesium/downloads) for released packages.

## Build

* Cesium uses [Ant](http://ant.apache.org/) for builds.  Ant is included in the Cesium repo, but it requires that the [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) be installed.
* From the root Cesium directory, run `./Tools/apache-ant-1.8.2/bin/ant combine`
   * On Windows: `.\Tools\apache-ant-1.8.2\bin\ant combine`

## Run

* Run `./Tools/apache-ant-1.8.2/bin/ant runServer` to start a web server, and browse to [[http://localhost:8080/]].
   * On Windows, `.\Tools\apache-ant-1.8.2\bin\ant runServer`

## Building and Running with Eclipse

If you have [Eclipse](http://www.eclipse.org/downloads/) you can run the above build from the GUI, and see output in the Eclipse console window.  The run menu looks like this:

<img src="screenshots/EclipseBuildMenu.jpg" />

## What Next?

Start hacking the examples, or read some more: the ten-minute [architecture overview] (https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture), the [reference documentation](http://cesium.agi.com/Documentation/), or the [contributor's guide](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Contributor%27s-Guide); which has detailed set-up instructions and is important for anyone interested in becoming a Cesium contributor.