Ideas for improving the main Cesium website, [cesium.agi.com](http://cesium.agi.com/).

* Fix links in our README.md when new site goes live.
* Our the website should be easy to deploy to.  Right now only a few of us know how to do it.  Why can't the whole thing (minus custom servers) be one repo?
* Many screenshots need improvements, for example, some images on the [features](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Features) page are too dark.
* Issue [#201](https://github.com/AnalyticalGraphicsInc/cesium/issues/201) - add Sandcastle links to the features page.  More generally, how can the website and Sandcastle work well together?
* Make demos more prominent: feature two or three on the main page.
* Add "Case studies", "User success stories", "Showcase", etc. to show off our user's work.
* Add color scheme to [reference doc](http://cesium.agi.com/Documentation/)?
* Polish demos (really a separate, orthogonal effort).  Details TBA.  Ideas welcome.

## Main Page Demo

Have the main page demo automatically runs with no UI to start this way it just looks like an animated picture.  It's a CZML file with the camera zooming around the globe:

   1. Maybe it starts in darkness with horizon view over Everest as the sun rises to light the sky.  (Eventually we can add light-snowfall once post-processing effects are in.) (Total time about 10 wall seconds)
   2. Then the camera zoom out to space and we see the GPS constellation, IIS, and other common objects the average person is familiar with.  If we want to get fancy we can fly to the ISS and have the Soyuz or Dragon undock and we follow that down to Earth.  (Total time, about 10 seconds)
   3. Then the camera zooms in for some "day in the life" style tracks close to the ground.  I'm not sure what, maybe it's all Philadelphia area car traffic or whatever cool ground based data we can get our hands on.

   * Maybe we can through in some mode transitions depending on where the camera is to showcase 2D/3D/Columbus.
   * When the user mousses over Cesium, the UI appears.  If they click anywhere, the animation stops and let's them take control and browse around.  They can start the animation over anytime they want, or browse anywhere they want.  We've transitioned from pretty-pictures to interactivity.
   * As Cesium features grow, the front-page grows.  We add models and more post-processing effects, maybe we eventually start it out with the Dragon launching into space with cool smoke and fire effects.  The goal is to showcase everything Cesium has in one beautiful 30 second demo that really plays to our strengths of time-dynamic global visualization.

## Old

* _Done_: General style and design improvements, e.g., using the Cesium colors as @kristiancalhoun did in his hackathon app.
* _Done_: Show; don't tell.  Let's have a small Cesium demo embedded in the main page.
* _Done_: Our github wiki has great content and is easy to edit, but it doesn't have the visibility, look, and feel that it should.  Let's sync our github wiki with the website, e.g., every time we update the wiki, a script updates the Cesium website.  Actually, we could do this with any repo, and change the github wiki to just link to the website so we don't have the same pages in two different spots.  We'll have to change some deep links elsewhere, but there aren't too many.
* _Done_: Add a blog as [discussed](https://groups.google.com/forum/#!topic/cesium-dev/tKul8BPg_DU) on the mailing list.
   * _Done_: It would be awesome if there are solid tools to integrate the writing process with github, but I'd be OK with WordPress, which is very well established.
