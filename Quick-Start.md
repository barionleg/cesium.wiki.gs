Getting started with a local copy of Cesium on Windows, Linux, and Mac is quick.

## Get the Code

* `git clone git@github.com:AnalyticalGraphicsInc/cesium.git`.

## Build

* Cesium uses [Ant](http://ant.apache.org/) for builds.  Ant is included in the Cesium repo, but it requires that the [Java](http://www.java.com/en/download/index.jsp) JDK be installed.
* From the root Cesium directory, run `./Tools/apache-ant-1.8.2/bin/ant combine`.

## Building with Eclipse

If you have [Eclipse](http://www.eclipse.org/downloads/) you can run the above build from the GUI, and see output in the Eclipse console window.  The run menu looks like this:

<img src="screenshots/EclipseBuildMenu.jpg" />

You'll need the Eclipse Java extensions to make this GUI build available, although Cesium itself is written in JavaScript.  Eclipse downloads typically don't include both Java and JavaScript in the same package.  After downloading "Eclipse IDE for Java developers", go to Help -> Install New Software..., click "Work with" and select the main Eclipse download site from the list, and select the JavaScript and web extensions for download and install.

## Run

* Run `./Tools/apache-ant-1.8.2/bin/ant runServer` to start a web server, and browse to http://localhost:8080.

## What Next?

Start hacking the examples, or read some more: the ten-minute [architecture overview](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture); the [contributor's guide](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Contributor%27s-Guide) with more details on building and running; or the [reference documentation](http://cesium.agi.com/Documentation/).