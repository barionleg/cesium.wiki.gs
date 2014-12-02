We are a community that encourages contributions.  Join us.  Here's how.

* [Get Started](#getstarted)
   * [Get the Code](#getthecode)
   * [Build the Code](#buildthecode)
   * [Set up Eclipse](#setupeclipse)
   * [Next Steps](#nextsteps)
* [Become an Expert](#becomeanexpert)
   * [Build Targets](#buildtargets)
   * [Optional Eclipse Configuration](#optionaleclipseconfiguration)
   * [Eclipse Tips](#eclipsetips)
   * [Test Tips](#testtips)
   * [Resources](#resources)
* [Contribute Code](#contributecode)

<a name="getstarted">
# Get Started

<a name="getthecode">
## Get the Code

Short version:
* No commit access? Fork and clone [cesium](https://github.com/AnalyticalGraphicsInc/cesium).
* Commit access? Clone [cesium](https://github.com/AnalyticalGraphicsInc/cesium) and make all changes in a branch.

Details
* Setup Git if it isn't already ([linux](https://help.github.com/articles/set-up-git#platform-linux) | [mac](https://help.github.com/articles/set-up-git#platform-mac) | [windows](https://help.github.com/articles/set-up-git#platform-windows)).
   * Make sure your SSH keys are configured ([linux](https://help.github.com/articles/generating-ssh-keys#platform-linux) | [mac](https://help.github.com/articles/generating-ssh-keys#platform-mac) | [windows](https://help.github.com/articles/generating-ssh-keys#platform-windows)).
   * Double-check your settings for name and email: `git config --get-regexp user.*`.
   * Recommended Git settings:
      * `git config --global push.default simple` - when running `git push`, only push the current branch (default in Git 2.0).
      * `git config --global pull.rebase preserve` - when pulling remote changes, rebase your local changes on top of the remote changes, to avoid unnecessary merge commits.
      * `git config --global fetch.prune true` - when fetching remote changes, remove any remote branches that no longer exist on the remote.
* Have commit access to cesium?
   * No
      * Fork [cesium](https://github.com/AnalyticalGraphicsInc/cesium).
      * Create a local repo of your fork, e.g., `git clone git@github.com:yourusername/cesium.git`.
   * Yes
      * Create a local cesium repo, e.g., `git clone git@github.com:AnalyticalGraphicsInc/cesium.git`
      * Make changes in a branch, e.g., `git checkout -b myFeature`.

<a name="buildthecode">
## Build the Code

Prerequisites:
 * Install [Java](http://www.java.com/en/download/manual.jsp) on your system.
 * Install [Node.js](http://nodejs.org/) on your system.

From the root Cesium directory, run:

```
./Tools/apache-ant-1.8.2/bin/ant combine runServer
```

Then browse to [http://localhost:8080/](http://localhost:8080/).

Details
* Cesium uses [Ant](http://ant.apache.org/) for builds.  Ant is included in the Cesium repo, but it requires that [Java](http://www.java.com/en/download/index.jsp) be installed.
* [Node.js](http://nodejs.org/) is also required by the build.  
* In the future, build functionality will move to Node.js and the need for Java will be removed.

For a default developer build, run Ant from the root Cesium directory:

```
./Tools/apache-ant-1.8.2/bin/ant
```

To run the HTTP server for testing, run:

```
./Tools/apache-ant-1.8.2/bin/ant runServer
```

To generate HTML documentation, run:

```
./Tools/apache-ant-1.8.2/bin/ant generateDocumentation
```

For all build options, see [Build Targets](#buildtargets) below.

<a name="setupeclipse">
## Set up Eclipse

We encourage contributors to use their IDE of choice, but many of us use Eclipse.  Here's how we set it up.

* Install [Java](http://www.java.com/en/download/manual.jsp) if it isn't already.
* Download the [Eclipse IDE](http://www.eclipse.org/downloads/) for Java Developers.  Extract to a directory of your choice.  Run it.

* Install additional Eclipse components: JavaScript Development Tools and Eclipse Web Developer Tools.
   * Help - Install New Software.  Work with: select *Luna* from the list.
   * Expand *Programming Languages*, check *JavaScript Development Tools*.
   * Expand *Web, XML, Java EE and OSGi Enterprise Development*, check *Eclipse Web Developer Tools*.
   * Next, Next, Accept, Finish, _wait_, No (we have more to install).

![The Java Development Tools installation dialog](indigo.png)

* Install the [JSHint](http://www.jshint.com/) plugin: 
   * Help - Install New Software.  Work with: `http://github.eclipsesource.com/jshint-eclipse/updates/`.
   * Check *JSHint*.  Next, Next, Accept, Finish, _wait_, OK, _wait_, Restart.

![The JSHint installation dialog](jshint.png)

* Run Eclipse. Close the Welcome page.

* Window - Preferences:
   * General - Editors - Text Editors.  Check Insert spaces for tabs.  Apply.
   * Web - CSS Files - Editor.  Switch the radio button to "Indent using spaces".  Change Indentation size to 4.  Apply.
   * Web - HTML Files - Editor.  Switch the radio button to "Indent using spaces".  Change Indentation size to 4.  OK.

![Configuring "Insert spaces for tabs"](tabs.png)

* Import Cesium into your workspace:  File - Import, General - Existing Projects into Workspace, Next.  Fill in the path to the root Cesium directory, Finish.

* Click the "Open Perspective" button in the upper right and select JavaScript.  You can then right-click on the Java perspective and close it.

* Window - Show View - Console.

Also consider the [Optional Eclipse Configuration](#optionaleclipseconfiguration) options below.

<a name="nextsteps">
## Next Steps

At this point you are ready to contribute.  Continue reading below for more details on the developer setup, or read about Cesium's [architecture](Architecture); check out the [roadmap](Roadmap); join the [forum](http://cesiumjs.org/forum.html); and start hacking.

<a name="becomeanexpert">
# Become an Expert

This section has additional information on our development tools.

<a name="buildtargets">
## Build Targets

The following targets can be built:
   * `build` - A fast, developer-oriented build that prepares the source tree for use as standard [Asynchronous Module Definition (AMD)](https://github.com/amdjs/amdjs-api/wiki/AMD) modules, suitable for running tests and most examples (some Sandcastle examples require running `combine`).  This runs automatically when saving files in Eclipse.
   * `combine` - Runs `build`, plus uses [Node.js](http://nodejs.org/) to run [the RequireJS optimizer](http://requirejs.org/docs/optimization.html) to combine Cesium and [the Almond AMD loader](http://requirejs.org/docs/faq-optimization.html#wrap) to produce all-in-one files in the `Build/Cesium` directory that expose the entire Cesium API attached to a single global Cesium object.  This version is useful if you don't want to use the modules directly with a standard AMD loader.
   * `minify` - Runs `combine`, plus [minifies](http://en.wikipedia.org/wiki/Minification_\(programming\)) Cesium.js using [UglifyJS2](https://github.com/mishoo/UglifyJS2) for a smaller deployable file.
   * `combineRelease` - Runs `combine`, plus uses the optimizer to remove debugging code that validates function input and throws DeveloperErrors.
   * `minifyRelease` - Runs `minify`, and removes debugging code.
   * `buildApps` - Builds the example applications (such as Cesium Viewer) to produce self-contained, minified, deployable versions in the `Build` directory.
   * `generateDocumentation` - Generates HTML documentation in `Build/Documentation` using [JSDoc 3](https://github.com/jsdoc3/jsdoc).  This step requires `npm install` to be run first.
   * `release` - A full release build that creates a shippable product, including building apps and generating documentation.
   * `instrumentForCoverage` - Runs [JSCoverage](http://siliconforks.com/jscoverage/) on the source tree to allow running tests with coverage information.  Use the link in index.html.  Currently Windows only.
   * `jsHint` - Runs [JSHint](http://www.jshint.com/) on the entire source tree.  If you use Eclipse, see below for how to run JSHint automatically as you develop.
   * `runServer` - Launches a [Node.js](http://nodejs.org/) HTTP server on [http://localhost:8080/](http://localhost:8080/) for easy access to the tests, examples, and documentation.  This also provides proxying for tile server providers that don't yet support [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) for retrieving tiles, which is required for use as textures.  To change the port, pass `-DrunServer.port=X`, where `X` is the desired port.
     * You can also run the server by running `node server.js`.  Pass `--help` for usage instructions.
   * `runPublicServer` - The same as `runServer` with the `-DrunServer.public=true` argument to allow for external connections.
   * `makeZipFile` - Builds a zip file containing all release files.  This includes the source tree (suitable for use from an AMD-aware application), plus the combined and minified Cesium.js files, the generated documentation, the test suite, and the example applications (in both built and source form).
   * `clean` - Removes all generated build artifacts.
   * `cloc` - Runs [CLOC](http://cloc.sourceforge.net/) to count the lines of code on the Source and Specs directories.  This requires [Perl](http://www.perl.org/) to execute.
   * `sortRequires` - Alphabetically sorts the list of required modules in every `js` file.

Specify the target(s) at the command line:

```
./Tools/apache-ant-1.8.2/bin/ant [target-name] [another-target-name] ...
```

For example, to build the release target and then start an HTTP server for testing, run:

```
./Tools/apache-ant-1.8.2/bin/ant release runServer
```

<a name="optionaleclipseconfiguration">
## Optional Eclipse Configuration

These steps are optional depending on your preference.

### Markdown Plugin

If you edit markdown files (.md) with Eclipse, installing the [Markdown plugin](http://www.winterwell.com/software/markdown-editor.php) is useful.

### GLSL Plugin

If you edit WebGL shader files (.glsl) with Eclipse, install GLShaders for GLSL syntax highlighting.  First exit Eclipse, then download [GLShaders](http://sourceforge.net/projects/glshaders/) and extract into Eclipse's dropins directory.

![The Eclipse dropins directory](glshaders.png)

### Git Plugin

Most of us use Git from the command-line, but there is also an Eclipse plugin.  The Eclipse package listed above includes this by default, but to install it in other Eclipse packages:
   * Help - Install New Software.  Work with: select *Luna* from the list.  
   * Expand *Collaboration*, check *Eclipse Git Team Provider*.
   * Next, Next, Accept, Finish, _wait_, Restart.

* Window - Preferences: Team - Git - Configuration
   * Verify Location in User Settings tab is set to .gitconfig in the default repository directory.
   * Verify Location in Systems Settings tab is set to {Installed/Git/Location}/etc/gitconfig.

* Right click on Cesium in the Script Explorer.  Team - Share project.  Select Git, Next.  Check Use or create repository in parent directory of project.  Finish.

<a name="eclipsetips">
## Eclipse Tips

* Use Ctrl-Shift-R to search and open files in the workspace.

![The Open Resource dialog](openresource.png)

* Use Ctrl-Shift-F to auto format selected code.

<a name="testtips">
## Test Tips

* To debug an individual test (spec), open the browser's debugger, e.g., Ctrl-Shift-I in Chrome, and click debug to the far right of the test.

![](debugJasmine.png)

Then, to step into the test, step into `stepIntoThis()`

![](stepIntoThis.png)

<a name="resources">
## Resources

* [WebGL Profiling Tips](http://cesiumjs.org/2014/12/01/WebGL-Profiling-Tips/)

<a name="contributecode">
# Contribute Code

See [CONTRIBUTING.md](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CONTRIBUTING.md).