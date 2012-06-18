We are a community that encourages contributions.  Join us.  Read about the engine's [architecture](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture); check out our [roadmap](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Roadmap); join the [development mailing list](https://groups.google.com/d/forum/cesium-dev); and start hacking.

## Getting the Code

Short version:
* No commit access? Fork and clone [cesium](https://github.com/AnalyticalGraphicsInc/cesium).
* Commit access? Clone [cesium](https://github.com/AnalyticalGraphicsInc/cesium) and make all non-trivial changes in a branch.

Details
* Setup git if it isn't already ([linux](http://help.github.com/linux-set-up-git/) | [mac](http://help.github.com/mac-set-up-git/) | [windows](http://help.github.com/win-set-up-git/)).
   * On Windows, `git config --global core.autocrlf true` (following the instructions above does this for you).  
   * On Linux/Mac, `git config --global core.autocrlf input` - see the [GitHub help on this topic](http://help.github.com/line-endings/).
   * Other recommended Git settings:
      * `git config --global push.default upstream` - when running `git push`, only push the current branch.
      * `git config --global branch.autosetuprebase always` - when pulling remote changes, rebase your local changes on top of the remote changes, to avoid unnecessary merge commits.
* Have commit access to cesium?
   * No
      * Fork [cesium](https://github.com/AnalyticalGraphicsInc/cesium).
      * Create a local repo of your fork, e.g., `git clone git@github.com:yourusername/cesium.git`
   * Yes
      * Create a local cesium repo, e.g., `git clone git@github.com:AnalyticalGraphicsInc/cesium.git`
      * Make non-trivial changes in a branch, e.g., `git branch myfeature`, and then `git checkout myfeature`

## Building the Code

Short version: from the root Cesium directory, run
<pre>
./Tools/apache-ant-1.8.2/bin/ant combine
./Tools/apache-ant-1.8.2/bin/ant runServer
</pre>
Then browse to [http://localhost:8080/](http://localhost:8080/).

Details
* Cesium uses [Ant](http://ant.apache.org/) for builds.  Ant is included in the Cesium repo, but it requires that the [Java](http://www.java.com/en/download/index.jsp) JDK be installed.
* For a default debug build, run Ant from the root Cesium directory:

<pre>
./Tools/apache-ant-1.8.2/bin/ant
</pre>

* The following targets can be built:
   * build - A fast, developer-oriented build that prepares the source tree for use as [Asynchronous Module Definition (AMD)](https://github.com/amdjs/amdjs-api/wiki/AMD) modules, suitable for running tests and most examples (at the moment the Sandbox example requires running "combine").  This runs automatically when saving files in Eclipse.
   * combine - Runs build, plus uses [NodeJS](http://nodejs.org/) to run [the RequireJS optimizer](http://requirejs.org/docs/optimization.html) and [the Almond AMD loader](http://requirejs.org/docs/faq-optimization.html#wrap) to produce an all-in-one file, Build\Cesium.js, that exposes the entire Cesium API attached to a single global Cesium object, if you don't want to use the modules directly with an AMD loader.
   * minify - Runs combine, plus [minifies](http://en.wikipedia.org/wiki/Minification_(programming\)) Cesium.js using [UglifyJS](https://github.com/mishoo/UglifyJS) for a smaller deployable file.  
   * release - Runs minify, plus generates documentation in Build\Documentation using [JSDoc 3](https://github.com/jsdoc3/jsdoc).
   * instrumentForCoverage - Runs [JSCoverage](http://siliconforks.com/jscoverage/) on the source tree to allow running tests with coverage information.  Use the link in index.html.  Currently Windows only.
   * runServer - Launches a [Jetty](http://jetty.codehaus.org/jetty/)-based HTTP server on http://localhost:8080 for easy access to the tests, examples, and documentation.  This also provides proxying for tile server providers that don't yet support [CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) for retrieving tiles, which is required for use as textures.
   * makeZipFile - Builds a zip file containing all release files.  This includes the Source directory (suitable for use from an AMD-aware application), plus the combined Cesium.js, and the Documentation files.
   * clean - Removes all generated build artifacts.
* For example, to build the release target and then start an HTTP server for testing, run:

<pre>
./Tools/apache-ant-1.8.2/bin/ant release
./Tools/apache-ant-1.8.2/bin/ant runServer
</pre>

Want something interesting to code?  See the [roadmap](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Roadmap) and start a discussion on the [development mailing list](https://groups.google.com/forum/#!topic/cesium-dev).

## Setting up Eclipse

Although we encourage contributors to use their IDE of choice, many of us use Eclipse.  Here is how we set it up:

* Install the [Java](http://www.java.com/en/download/index.jsp) JRE if it isn't already.
* Download the [Eclipse IDE](http://www.eclipse.org/downloads/) for JavaScript Web Developers.  Extract to a directory of your choice.  Run it.
* Install the [JSHint](http://www.jshint.com/) plugin: 
   * Help - Install New Software.  Work with: http://github.eclipsesource.com/jshint-eclipse/updates/.
   * Check JSHint.  Next, Next, Accept, Finish, _wait_, Not Now (we have more to install).

![The JSHint installation dialog](jshint.png)

* Install the Java Development Tools (for Ant support) and EGit.
   * Help - Install New Software.  Work with: select Indigo from the list.  
   * Expand Programming Languages, check Eclipse Java Development Tools.  
   * Expand Collaboration, check Eclipse EGit.  
   * Next, Next, Accept, Finish, _wait_, Not Now.

![The Java Development Tools installation dialog](indigo.png)

* Install GLShaders for GLSL syntax highlighting:  Exit Eclipse.  Download [GLShaders](http://sourceforge.net/projects/glshaders/) and extract into Eclipse's dropins directory.

![The Eclipse dropins folder](glshaders.png)

* Run Eclipse. Close the Welcome page.

* Window - Preferences - Team - Git - Configuration
    * Verify Location in User Settings tab is set to .gitconfig in the default repository folder.
    * Verify Location in Systems Settings tab is set to {Installed/Git/Location}/etc/gitconfig.

* Window - Show View - Console.

* Window - Preferences.  General - Editors - Text Editors.  Check Insert spaces for tabs.  OK.

![Configuring "Insert spaces for tabs"](tabs.png)

* Import Cesium into your workspace:  File - Import, General - Existing Projects into Workspace, Next.  Fill in the path to the root Cesium directory, Finish.

* Right click on Cesium in the Script Explorer.  Team - Share project.  Select Git, Next.  Check Use or create repository in parent folder of project.  Finish.

* Configure the problems tab.  The Eclipse JavaScript validator has some bugs that report incorrect warnings.  Click the down arrow on the right-hand side of the Problems tab, click Configure Contents.  Uncheck Show all items, Click New, then Rename the new item to Cesium.  Change the Text filter to "doesn't contain" "Type mismatch: ".  OK.

![Opening the Configure Contents dialog](configureContents.png)

![Creating a new filter](configureContents2.png)

## Development Tips

* In Eclipse, use Ctrl-Shift-R to search and open files in the workspace.

![The Open Resource dialog](openresource.png)

* To debug an individual test (spec), open the browser's debugger, e.g., Ctrl-Shift-I in Chrome, and click debug to the far right of the test.

![](debugJasmine.png)

Then, to step into the test, step into `stepIntoThis()`

![](stepIntoThis.png)

* Use [www.webglreport.com](http://www.webglreport.com) to see if WebGL is supported, and if so, what is exactly supported.  For more goodness, including the ANGLE revision, browse to chrome://gpu-internals/ in Chrome.

* Keep your video card drivers up to date.  [NVIDIA](http://www.nvidia.com/Download/index.aspx) | [AMD](http://support.amd.com/us/gpudownload/Pages/index.aspx).

* For WebGL debugging such as stepping through draw calls, viewing textures and vertex buffers, etc., use the [WebGL Inspector](http://benvanik.github.com/WebGL-Inspector/).

* To run without [ANGLE](http://code.google.com/p/angleproject/) (Windows-only)
   * Chrome:  Run with the --use-gl=desktop argument.  Make sure you close all Chrome windows before starting.
   * Firefox:  Browse to about:config and set webgl.prefer-native-gl to true.

* For performance testing, turn off [vsync](http://hardforum.com/showthread.php?t=928593)
   * In the driver, e.g., the NVIDIA Control Panel or the Catalyst Control Center.
   * Also turn off VSync in Chrome: browse to chrome://flags/ and check Disable GPU VSync.

* For an FPS counter in Chrome, browse to chrome://flags/ and check FPS counter.  Create a FPS counter in Cesium with `PerformanceDisplay`

## Contributing Code

* Send us a [pull request](http://help.github.com/send-pull-requests/).  We'll promptly [review](Code-Review-Tips) it, provide feedback, and merge it.
* Before we can merge, we require a [Contributor License Agreement](http://producingoss.com/en/copyright-assignment.html#copyright-assignment-cla) (CLA).  This can be emailed to cla@agi.com, and only needs to be completed once.  The CLA ensures that you retain copyright to your contributions, and that we have the right to use them.  There is a CLA for [individuals](http://www.agi.com/licenses/individual-cla-agi-v1.0.txt) and [corporations](http://www.agi.com/licenses/corporate-cla-agi-v1.0.txt).  Please email completed CLAs and related questions to cla@agi.com.
* Please make sure
   * Your code follows the [coding conventions](https://github.com/AnalyticalGraphicsInc/cesium/wiki/JavaScript-Coding-Conventions).
   * Your code passes [JSHint](http://www.jshint.com/).  We use the JSHint Eclipse plugin so it runs automatically when we save.
   * To include tests with excellent code coverage for new features.  We use [Jasmine](http://pivotal.github.com/jasmine/) for writing tests.  Run them by browsing to http://localhost:8080/Specs/SpecRunner.html.  Verify all  new and existing tests pass.  For bonus points, test Chrome, Firefox, and other browsers supporting WebGL.
   * To include reference documentation with code examples when adding new public functions and properties.  We use [JsDoc Toolkit](http://code.google.com/p/jsdoc-toolkit/).  Check out the [tag reference](http://code.google.com/p/jsdoc-toolkit/wiki/TagReference).
   * To update [CHANGES.md](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CHANGES.md) if the change is something users should know about, and to update [LICENSE.md](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/LICENSE.md) if third-party libraries were added or removed.
* If you have commit access, delete the branch if you are no longer using it.