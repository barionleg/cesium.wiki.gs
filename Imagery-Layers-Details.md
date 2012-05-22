Design and implementation ideas for imagery layers.

## General Comments

* Breaking changes are OK; in fact, we expect some.
* Layers should work in 3D and 2D.
* Streaming imagery is not covered particularly well by our tests.  With this feature, we should also improve the tests.

## Initial Features

* Ability to z-order multiple images - from different tile providers - on the globe and map.  The interface should be consistent with the [composite primitive](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/Source/Scene/CompositePrimitive.js), i.e., `add`, `remove`, `removeAll`, `contains`, `bringForward`, `bringToFront`, `sendBackward`, `sendToBack`, `get`, and `getLength`.  The composite primitive can change if necessary.  
* Each layer should have an `alpha` value for blending.  0.0 is transparent; 1.0 is opaque.
* A layer should not have to cover the entire globe; they can be restricted to an extent as is common with WMS.
* Many APIs can restrict the zoom level.  I assume it's useful - it's certainty trivial - but I'm not sure why.  Performance?

## Full Features

* Ensure reasonable consistency between imagery layers and terrain providers.
* Layer all ground primitives - at least polylines and polygons - seamlessly with imagery.  Many people think in terms of vector layers, KML layers, etc.  We should support this, but shouldn't lose sight of our focus on air and space where this paradigm breaks down.
* Do we need layers for night lights?  Why not layer a day image over night?  In general, we need to revisit the architecture for night, bump, specular, clouds, etc.  Clouds may happen sooner rather than later.
* Show/hide based on time?  This may be done above Scene, but we need to think about it.  More general _display conditions_ could also be useful.

## Initial Implementation

* `CentralBody.dayTileProvider` can be replaced with something like `CentralBody.dayLayers`, which would have an interface similar to `CompositePrimitive`.
* In `render()`, layers can be drawn in z-order from bottom to top, then lay down the depth plane.  Careful - currently, tiles in each layer need to be sorted back to front from the viewers perspective since they are not depth tested.  This will change as we implement multi-frustums and terrain.
   * Use blending in the render state to support layer alpha.
   * The tessellation among layers will be different when the layer extents do not match.  This will create artifacts for horizon views.  To fix this, see comment on decoupling below.
   * This approach also have performance implications:
      * Lots of draw calls.
      * Lots of overdraw.  For an ellipsoid with backface culling, the depth complexity should be one.  Here, it will be the number of layers.
      * Potential solution below.

## Full Implementation

* TBA: Occlude opaque layers

* Geometry (ellipsoid or terrain) and textures should be decoupled.  That is, first, tiles are chosen based solely on geometric level of detail given the view parameters.  Then, textures are chosen based on their level of detail.  Finally, each tile is rendered with multi-texturing and multiple texture matrices to position each texture on the geometry.  More thoughts:
   * We may need multiple sets of texture coordinates; not just texture matrices.
   * Before multi-texturing, this would be done with multiple passes.  Multi-texturing imposes a limit on the number of layers we can support, but 99% of WebGL users support 16 texture units in the fragment shader.  See the [stats](http://webglstats.com/).
   * Determining what textures overlap what tiles can burn a lot of CPU.  An r-tree can be used to make this query fast (at the expense of creating and maintaining the tree, of course).  Perhaps there are already JavaScript r-tree implementations, or a simpler spatial data structure will suffice.  We also need to look at related r-tree patents to make sure we can use it.  Papers:
      * [R-Trees.  A Dynamic Index Structure for Spatial Searching](http://postgis.refractions.net/support/rtree.pdf).  1984.
      * [The R*-tree: An Efficient and Robust Access Method for  Points and Rectangles](http://infolab.usc.edu/csci587/Fall2011/papers/p322-beckmann.pdf).  1990.
      * [Priority r-tree](http://www.cse.ust.hk/~yike/prtree/).  2004.

## Other APIs with Layers
   * Insight3D - [Imagery Overlay](http://www.agi.com/resources/help/online/AGIComponents/Programmer's%20Guide/Overview/Graphics/GlobeOverlays/Imagery.html) and [Web Imagery Overlays](http://www.agi.com/resources/help/online/AGIComponents/Programmer's%20Guide/Overview/Graphics/GlobeOverlays/WebImagery.html).
   * OpenWebGlobe - [Tutorial](http://wiki.openwebglobe.org/doku.php?id=tutorial:webgl0103) and [reference](http://wiki.openwebglobe.org/doku.php?id=reference).
   * WebGL Earth - See `WebGLEarth.Map` in the [API](http://www.webglearth.org/api).
   * ReadyMap - [Layers demo](http://demo.pelicanmapping.com/rmweb/webgl/tests/twolayers.html).
   * Glob3 - [Layers example](http://ami.dis.ulpgc.es/glob3m/index.php?id=4&example=layers).
   * OpenLayers - [doc](http://docs.openlayers.org/library/layers.html); [reference doc](http://dev.openlayers.org/releases/OpenLayers-2.11/doc/apidocs/files/OpenLayers/Layer-js.html); and lots of [examples](http://openlayers.org/dev/examples/) such as [layer opacity](http://openlayers.org/dev/examples/layer-opacity.html).
   * Leaflet - [doc](http://leaflet.cloudmade.com/reference.html) and [examples](http://leaflet.cloudmade.com/examples.html).