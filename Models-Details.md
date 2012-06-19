Design and implementation ideas for models.

## Features

* COLLADA features
   * Common Profile - most models today use the common profile AFAIK.  We need to generate shaders based on their materials.
   * GLES2 - Recommended for use with WebGL.  Do any models use it yet?
   * COLLADA FX - for writing shaders for things like metal, foil, etc.
   * COLLADA Animation - for articulating things like satellite solar panels and aircraft landing gear.
* Work in Columbus view.  The model scale will need to be adjusted - and will be relative to the projection
* Work in 2D.  Render model to texture from top-down view; lay over top the 2D map as a billboard.  The model will appear lit and changes in orientation, e.g., banked aircraft turns, will be seen.  Awesome.
* Interaction with CZML
   * CZML references external models.
   * Time-varying CZML can manipulate model animation (articulations), materiel properties, etc.
   * CZML includes a subset of model JSON, e.g., geometry (or all of it)?

## Format

* Read COLLADA client-side?
* Or convert COLLADA (and other model formats) to JSON server-side?
   * Use and contribute back to an open-source converter?
   * Use the most standard JSON format.  Will Khronos propose a COLLADA JSON standard?
   * Go beyond JSON?  Use typed arrays for vertex data.  Take a close look at [webgl-loader](http://code.google.com/p/webgl-loader/) for mesh compression.
   * The converter should be a library for developers; a command-line tool for scripting; and a hosted web service for the rest of the world.
   * From the end-user's perspective, conversion to JSON should be transparent, e.g., if they drag and drop a COLLADA model, it is sent to the service, and JSON is sent back.

## Rendering Optimizations

I believe we can have a very fast implementation; perhaps even faster than many C++ ones.  Bold words, I know.

These optimizations could be on the fly or as a preprocess in the content pipeline (using node.js).  Doing it on the fly ensures that no mater how the model is authored, we still get the rendering performance benefit.

* If a mesh has the same vertex layout as another mesh, they should be combined into a single vertex buffer, and, possibly even a single draw call if the materials are the same.
* If transforms are static, the tree can be flattened and positions adjusted so there are less batch-breaking model transform uniforms set, and, therefore, less draw calls.
* Reorder for the vertex cache.
* Auto generate discrete geometric LOD using [quadric error metrics](http://mgarland.org/archive/cmu/quadrics/).  Perhaps even stream just the lowest LOD to the client to start.  Can we also use this code for polyline simplification?
* Reduce the size of large textures that are not likely to take up a lot of screen space.
* Use the [COLLADA Refinery](https://collada.org/mediawiki/index.php/COLLADA_Refinery)?

These optimizations will be done at run-time:

* Sort by material, perhaps create buckets on model load.
* Coarse front-to-back sort.

## Content

We recognize the need to support the widest possible content, therefore, we need to transparently support loading models from all major web-based model repositories whose terms of service allow.

* [rest3d](http://rest3d.wordpress.com/about-2/) aims to define a standard web API for accessing 3D assets.  It sounds like a great effort, but I haven't seen any activity since 2011.
* [OurBricks](http://www.ourbricks.com/) "connects people who need great 3D content with those who can create it."  Great effort; worth a close look at their [API](https://github.com/ourbricks/ourbricks-api-examples/wiki/API-Documentation).  Perhaps they would integrate with our JSON converter and serve the format directly, or we could use a proxy if the TOS allow.
* [p3d.in](http://p3d.in/) is also for sharing 3D models.  Artists can upload .obj files and embed the viewer in a webpage, but I'm not sure if there is any API for accessing their models.
* [Sketchfab](http://sketchfab.com/) is similar to p3d.in in that it is for sharing 3D models and embedding them in webpages.  However, they have an [API](http://sketchfab.com/api), but it looks like it is only for sending content.  Perhaps they are open to an API for reading models like OurBricks.  They support a lot of [formats](http://sketchfab.com/faq).
* [US Government ADL 3D Repository](http://3dr.adlnet.gov/) - Very relevant content for Cesium; lots of satellite, aircraft, and ground vehicle models.  Requires login to download.  Models are available under public domain or CC license.  Only 354 total models.  No REST API.
* [Google 3D Warehouse](http://sketchup.google.com/3dwarehouse/) - lots of models.  Need to look at the [terms of service](http://sketchup.google.com/intl/en/3dwh/preview_tos.html).  Not sure about an API.  It would be cool to have a WebGL browser for this though.
* [3DVia](http://www.3dvia.com/search/?search[file_types]=1) - Looks good.  Worth a closer look.  Need to look at what is free and what is paid.

## Tools

* COLLADA to JSON converter.  Most likely use [BadgerFish-JSON](http://www.sklar.com/badgerfish/).
* Model editor - load models into a Cesium scene, tweak their animations, etc.
   * Perhaps part of Sandcastle.
* Useful to integrate with existing WebGL modeling tools?  Do any of these have APIs for accessing models?
   * [3DTin](http://www.3dtin.com/)
   * [Bevelity](http://www.bevelity.com/)

## Conversion to JSON

### Existing COLLADA to JSON converters

Need to contact developers and look more carefully at each of these JSON formats.

* CubicVR.js [XML -> BF-JSON](https://github.com/cjcliffe/CubicVR.js/blob/master/source/CubicVR.Utility.js).
* [scenejs-pycollada](http://scenejs.wikispaces.com/scenejs-pycollada) - A python script to convert from COLLADA to SceneJS.
   * Example [JSON](http://scenejs.org/dist/v2.0.0/extr/examples/seymour-plane/seymour-plane.js) from the [Seymour Plane Demo](http://scenejs.org/dist/v2.0.0/extr/examples/seymour-plane/index.html).
   * No activity in six months, but the features are clearly described in README.md on the [github](https://github.com/xeolabs/scenejs-pycollada) page.
* [OpenWebGlobe](https://github.com/OpenWebGlobe/ColladaToJSON) - A python script to convert from COLLADA to OpenWebGlobe's JSON format.  Uses [pycollada](https://github.com/pycollada/pycollada).  MIT license.
   * Not much actively recently.  Need to find out how far along it is.
* O3D's [COLLADA to JSON converter](http://code.google.com/p/o3d/wiki/ColladaConverter).  A [blog post](http://o3d.blogspot.com/2009/04/why-json-rulez.html) on their rational - more flexibility.  Doesn't look like it's been touched in a while.

## Client-side COLLADA

Some libraries read COLLADA directly without converting it.

* Three.js reads COLLADA [client-side](https://github.com/mrdoob/three.js/blob/master/examples/js/loaders/ColladaLoader.js).  Looks like they've been working on it recently.  Three.js also has a [JSON format](https://github.com/mrdoob/three.js/wiki/JSON-Model-format-3.0), including some Python [exporters](https://github.com/mrdoob/three.js/tree/master/utils/exporters), that is worth a close look.
* [Odin](https://github.com/operasoftware/Odin) reads COLLADA client-side or a derived run-time format.
* SpiderGL - [example](http://spidergl.org/example.php?id=10).
* C3DL - [doc](http://www.c3dl.org/wp-content/documentation/2.0_user_docs/symbols/c3dl.Collada.html), [tutorial](http://www.c3dl.org/index.php/tutorials/tutorial-4-models/), [code](https://github.com/cathyatseneca/c3dl/tree/master/c3dl/collada).
* I believe [GLGE](http://statico.github.com/webgl-glge-game-part-1.html) also reads COLLADA client-side.

## Resources

* [COLLADA & WebGL](http://www.slideshare.net/remi_arnaud/collada-webgl) - Skip to Slide 43.