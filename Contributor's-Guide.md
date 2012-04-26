We are a community that encourages contributions.  Join us.  Check out our [roadmap](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Roadmap); join the [development mailing list](https://groups.google.com/d/forum/cesium-dev); and start hacking.

## Getting the Code

* Setup git if it isn't already ([linux](http://help.github.com/linux-set-up-git/) | [mac](http://help.github.com/mac-set-up-git/) | [windows](http://help.github.com/win-set-up-git/)).
* Fork [cesium](https://github.com/AnalyticalGraphicsInc/cesium).
* Create a local repo of your fork, e.g., `git clone git@github.com:yourusername/cesium.git`.
* If you make changes you would like to contribute back, send us a [pull request](http://help.github.com/send-pull-requests/).

## Building the Code

* Cesium uses [Ant](http://ant.apache.org/) for builds.  Ant is included in the Cesium repo, but it requires that the [Java](http://www.java.com/en/download/index.jsp) JDK be installed.
* For a default debug build, run:

<pre>
./Tools/apache-ant-1.8.2/bin/ant -buildfile ./Cesium/build.xml
</pre>

* The following targets can be built:
   * build - A fast, developer-oriented build that prepares the source tree for use as [Asynchronous Module Definition (AMD)](https://github.com/amdjs/amdjs-api/wiki/AMD) modules, suitable for running tests and most examples (at the moment the Sandbox requires running "combine").  This runs automatically when saving files in Eclipse.
   * combine - Runs build, plus uses [NodeJS](http://nodejs.org/) to run [the RequireJS optimizer](http://requirejs.org/docs/optimization.html) and [the Almond AMD loader](http://requirejs.org/docs/faq-optimization.html#wrap) to produce an all-in-one file, Build\Cesium.js, that exposes the entire Cesium API attached to a single global Cesium object, if you don't want to use the modules directly with an AMD loader.
   * minify - Runs combine, plus [minifies](http://en.wikipedia.org/wiki/Minification_(programming\)) Cesium.js using [UglifyJS](https://github.com/mishoo/UglifyJS) for a smaller deployable file.  
   * release - Runs minify, plus generates documentation in Build\Documentation using [JSDoc 3](https://github.com/jsdoc3/jsdoc).
   * instrumentForCoverage - Runs [JSCoverage](http://siliconforks.com/jscoverage/) on the source tree to allow running tests with coverage information.  Use the link in index.html.  Currently Windows only.
   * runServer - Launches a [Jetty](http://jetty.codehaus.org/jetty/)-based HTTP server on http://localhost:8080 for easy access to the tests, examples, and documentation.  Also provides proxying for tile server providers that don't yet support [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) for retrieving tiles, which is required for use as textures.
   * clean - Removes all generated build artifacts.
* For example, to build the release target:

<pre>
./Tools/apache-ant-1.8.2/bin/ant -buildfile ./Cesium/build.xml release
</pre>

## Setting up Eclipse

Although we encourage contributors to use their IDE of choice, many of us use Eclipse.  Here is how we set it up:

* Install the [Java](http://www.java.com/en/download/index.jsp) JRE if it isn't already.
* Download the [Eclipse IDE](http://www.eclipse.org/downloads/) for JavaScript Web Developers.  Extract to a directory of your choice.  Run it.
* Install the [JSHint](http://www.jshint.com/) plugin: Help - Install New Software, Work with: http://github.eclipsesource.com/jshint-eclipse/updates/.  Check JSHint.  Next, Next, Accept, Finish, _wait_, Not Now (we have more to install).

![](jshint.png)

* Install the Java Development Tools (for Ant): Help - Install New Software, Work with: select Indigo from the list.  Expand Programming Languages, check Eclipse Java Development Tools.  Expand Collaboration, check EGit.  Next, Next, Accept, Finish, _wait_, Not Now.

![](indigo.png)

* Install GLShaders for GLSL syntax highlighting:  Exit Eclipse.  Download [GLShaders](http://sourceforge.net/projects/glshaders/) and extract into eclipse's dropins directory.

![](glshaders.png)

* Run Eclipse. Close the Welcome page.

* Window - Show View - Console.

* Window - Preferences.  General - Editors - Text Editors.  Check Insert spaces for tabs.  OK.

![](tabs.png)

* Import Cesium into your workspace:  File - Import, General - Existing Projects into Workspace, Next.  Fill in the path to the Cesium\Cesium directory, Finish.

* Right click on Cesium in the Script Explorer.  Team - Share project.  Select Git, Next.  Check Use or create repository in parent folder of project.  Finish.

## Building with Eclipse

TBA