Design and implementation ideas for models.

## Features

### General Model Features

* COLLADA features
   * Common Profile - most models today use the common profile AFAIK.  We need to generate shaders based on their materials.
   * GLES2 - Recommended for use with WebGL.  Do any models use it yet?
   * COLLADA FX - for writing shaders for things like metal, foil, etc.
   * COLLADA Animation
      * Programmable control over articulations for animating things like satellite solar panels and aircraft rudder and landing gear; wheels on ground vehicles; communication dishes; rigs for robot arms; rigid body dynamics driving explosions; and skinning deformations.
      * Time-tagged key-frames for walk cycle, run cycle, ISS robotic arms, bay of shuttle, etc.
      * Do not need physics now if we have key-frame animation.
   * Skinning
   * Is LOD part of the model or part of the REST API requesting it?
* Work in Columbus view.  The model scale will need to be adjusted - and will be relative to the projection
* Work in 2D.  Render model to texture from top-down view; lay over top the 2D map as a billboard.  The model will appear lit and changes in orientation, e.g., banked aircraft turns, will be seen.  Awesome.
* COLLADA to WebGLTF conversion (see below)
   * The converter should be a library for developers; a command-line tool for scripting; and a hosted web service for the rest of the world.
   * From the end-user's perspective, conversion to WebGLTF should be transparent, e.g., if they drag and drop a COLLADA model, it is sent to the service, and WebGLTF is sent back.
* Interaction with CZML
   * CZML references external models.
   * Time-varying CZML can manipulate model animation (articulations), materiel properties, etc.
   * CZML includes a subset of model JSON, e.g., geometry (or all of it)?

### Cesium-Specific Features

These are engine/app level features.

* Attach points.  _General feature: need access to node's transform (to root) by name.  The transform can change over time due to animation, user interaction, etc._
   * Attach vapor trails to the back of a launch vehicle.
   * Attach a sensor to the front of a UAV.
* Pointing.  _Need Cesium-level semantics for sun, other objects, etc. to control direction and up vectors_.
   * _General_: Point a quad toward the camera, e.g., foliage, explosion, Rudolph's nose, etc.
   * Point satellite solar panels to the sun.
   * Point sensor on aircraft to a ground station.


xxxx

## WebGL Transmission Format

_Server-side_: convert COLLADA to [WebGLTF](https://github.com/KhronosGroup/collada2json/wiki/WebGLTF) using [collada2json](https://github.com/KhronosGroup/collada2json).

_Client-side_: use collada2json's WebGL library to read WebGLTF.

Contribute back to collada2json using our [fork](https://github.com/AnalyticalGraphicsInc/collada2json).

There are already converters to convert many different formats to COLLADA.

## Server-Side Pipeline

_This pipeline has significant overlap with the collada2json transformations.  We will collaborate with them._

Do the least amount of work possible client-side.  The server-side pipeline prepares the model to render:

Required:
   * Triangulate - Convert polygons (`<polygons>` and `<polylist>`) into triangle lists.  Since this only adds indices, it does not dramatically increase the payload. [#42](https://github.com/KhronosGroup/collada2json/issues/42)
   * Unify indices - In COLLADA, each attribute may be indexed separately.  Unify these so one index refers to all vertex attributes.
   * Split meshes to fit in unsigned short indices - This may need to be done in the optimizations instead if we are combining meshes.
   * Generate shaders - Create GLSL shaders for models using the Common Profile (fixed function), which is most models.
   * Convert textures - Convert image files to a format supported by the browser, e.g., .tiff to .png.

Optional for performance (some of these _could_ also be done client-side):

* Compression, e.g., [webgl-loader](http://code.google.com/p/webgl-loader/).  Also see [X3D Binary Compression](http://www.web3d.org/wiki/index.php/X3D_Binary_Compression_Capabilities_and_Plans).
* Flatten tree:  if transforms are static, the tree can be flattened and positions adjusted so there are less batch-breaking model transform uniforms set, and, therefore, less draw calls. [#30](https://github.com/KhronosGroup/collada2json/issues/30)
* Auto generate discrete geometric LOD using [quadric error metrics](http://mgarland.org/archive/cmu/quadrics/).  Perhaps even stream just the lowest LOD to the client to start.
* Vertices
   * Reorder for the pre- and post- vertex-shader caches (we already have JavaScript [code](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/Source/Core/Tipsify.js) to do this client-side).
   * Adjust vertex formats, e.g., `float` to `unsigned byte` for colors.
* Textures
   * Reduce the size of large textures that are not likely to take up a lot of screen space.
   * Combine textures into a texture atlas to help batching.
   * Compress textures.
* Consider [meshtool](https://github.com/pycollada/meshtool) and the [COLLADA Refinery](https://collada.org/mediawiki/index.php/COLLADA_Refinery)?

The last step in the pipeline is to convert from COLLADA to WebGLTF.

## Client-Side Optimizations

Most optimizations are done server-side as part of the content pipeline.  However, a few optimizations can only be done at runtime when rendering:

* Sort by material, perhaps create buckets on model load.
* Coarse front-to-back sort.

## Content

We recognize the need to support the widest possible content, therefore, we need to transparently support loading models from all major web-based model repositories whose terms of service allow.

* [rest3d](http://rest3d.wordpress.com/about-2/) aims to define a standard web API for accessing 3D assets.
* [3dpie](http://www.opengeospatial.org/projects/initiatives/3dpie)
* [Sketchfab](http://sketchfab.com/) is similar in that it is for sharing 3D models and embedding them in webpages.  They have an [API](http://sketchfab.com/api), but it is only for sending content; retrieving content is on their roadmap.  Perhaps they are open to an API for reading models like OurBricks.  They support a lot of [formats](http://sketchfab.com/faq).
* [OurBricks](http://www.ourbricks.com/) "connects people who need great 3D content with those who can create it."  Great effort; worth a close look at their [API](https://github.com/ourbricks/ourbricks-api-examples/wiki/API-Documentation).  
* [p3d.in](http://p3d.in/) is also for sharing 3D models.  Artists can upload .obj files and embed the viewer in a webpage, but I'm not sure if there is any API for accessing their models.
* [NASA 3D Models](http://www.nasa.gov/multimedia/3d_resources/models.html)
* [OpenBuildingModels](http://wiki.openstreetmap.org/wiki/OpenBuildingModels)
* [US Government ADL 3D Repository](http://3dr.adlnet.gov/) - Very relevant content for Cesium; lots of satellite, aircraft, and ground vehicle models.  Requires login to download.  Models are available under public domain or CC license.  Only 354 total models.  No REST API.
* [verold](http://studio.verold.com/)
* [Google 3D Warehouse](http://sketchup.google.com/3dwarehouse/) - lots of models.  Need to look at the [terms of service](http://sketchup.google.com/intl/en/3dwh/preview_tos.html).  Not sure about an API.  It would be cool to have a WebGL browser for this though.
* [3DVia](http://www.3dvia.com/search/?search[file_types]=1) - Looks good.  Worth a closer look.  Need to look at what is free and what is paid.
* [TFT Labs' JSON3D Gallery](http://json3d.tftlabs.com/)
* [AGI 3D Models](http://www.agi.com/resources/downloads/data/3d-models/)
* [COLLADA Test Model Bank](http://www.collada.org/owl/) - models for testing

Will we be able to render models directly from the provider's APIs or do we need to proxy them for conversion?  If we proxy, do the TOS allow us to cache?

## Tools

* Model viewer/editor - load models into a Cesium scene, tweak their materials, animations, etc.
   * Server with file-watcher that converters saved COLLADA to WebGL TF and uses web sockets to push to viewer.
* Useful to integrate with existing WebGL modeling tools?  Do any of these have APIs for accessing models?
   * [3DTin](http://www.3dtin.com/)
   * [Bevelity](http://www.bevelity.com/)
* [JSModeler](https://github.com/kovacsv/JSModeler) is a JavaScript framework to create and visualize 3D models.
* [COLLADA-CTS](https://github.com/KhronosGroup/COLLADA-CTS)

## Unorganized Hackathon Notes

### Client

* Add support for our material system.

### Server

* Models should probably be a CZML extension since if they were core, [WebGL TF](https://github.com/KhronosGroup/collada2json/wiki/WebGLTF) would require that CZML clients support WebGL, or at least support GLSL for the shaders.