Design and implementation ideas for imagery layers.

## Already implemented

* Ability to z-order multiple images - from different tile providers - on the globe and map.  The interface should be consistent with the [composite primitive](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/Source/Scene/CompositePrimitive.js), i.e., `add`, `remove`, `removeAll`, `contains`, `bringForward`, `bringToFront`, `sendBackward`, `sendToBack`, `get`, and `getLength`.  However, the composite primitive interface can change if necessary.  
* Each layer should have an `alpha` value for blending with the layer underneath.  0.0 is transparent; 1.0 is opaque.
* A layer should not have to cover the entire globe; they can be restricted to an extent as is common with WMS.
* In `render()`, layers can be drawn in z-order from bottom to top, then lay down the depth plane.  Currently, tiles in each layer need to be sorted back-to-front from the viewer's perspective since they are not depth tested.  (Actually, we should look more carefully at the motivation for this sorting).  This will change as we implement multi-frustum and terrain.
   * Use blending in the render state to support layer alpha.
   * The tessellation among layers will be different when the layer extents or (currently) image maximum resolution do not match.  This will create artifacts for horizon views.  To fix this, see comment on decoupling below.  If the geometric LOD is high enough, we may not notice the artifacts.
   * This approach also has performance implications:
      * Lots of draw calls creates CPU overhead.
      * Lots of overdraw.  For an ellipsoid with backface culling, the depth complexity should be one.  Here, it will be the number of layers that overlap a pixel.
      * Potential tile requests for tiles completely occluded by opaque layers higher in the z-order.
      * Lots of extra memory used for duplicate or similar geometry tiles.
      * Solution idea below.
* The credit, e.g., logo, for multiple layers will need to be shown.  We should avoid duplicates, e.g., don't show the same credit twice if two layers from the same provider are shown.  Down the road, we need the ability for view-dependent credits when a layer comes from several sources.
* For even better performance (reduced number of draw calls) and to fix artifacts between layers, we should decouple geometry (ellipsoid or terrain) and textures.  First, tiles are chosen based solely on geometric level of detail given the view parameters.  Then, textures are chosen based on their level of detail.  Finally, each tile is rendered with multi-texturing and multiple texture matrices to position each texture on the geometry.
   * Before multi-texturing, this would be done with multiple passes.  Multi-texturing imposes a limit on the number of layers we can support, but 99% of WebGL users have 16 texture units in the fragment shader.  See the [stats](http://webglstats.com/).
   * Searching for what textures overlap a tile will burn a lot of CPU - and probably miss L2 everywhere - even with a spatial data structure.  However, we should be able to exploit temporal coherence; if a tile is rendered in one frame, it is likely to be rendered in the next frame with the same overlapping textures.
      * We could also have a fast path when tiles and texture providers line up, i.e., each tile has one corresponding texture.  This is, for example, how Google Earth and most virtual globes work AFAIK.

## Future Ideas

* Many APIs can restrict the zoom level.  I assume it's useful - it's certainty trivial to expose in our code - but I'm not sure of the use cases.  Performance?
* Layer primitives on the ground - at least polylines and polygons - seamlessly with imagery.  Many people think in terms of vector layers, KML layers, etc.  Everything is a layer.  We should support this, but shouldn't lose sight of our focus on air and space where this paradigm breaks down.
* Do we need layers for night lights?  Why not layer a day image over night?  In general, we need to revisit the architecture for night, bump, specular, clouds, etc.  Clouds may happen sooner rather than later.
* Image processing to _fix_ images, e.g.,
   * Bing Maps imagery is really dark, so brighten it.
   * Landsat imagery is usually 11 or 12 bits, and loses its dynamic range when dropped to 8-bits.
   * For Landsat multispectral imagery, we might want to color one band.
   * Histogram, gamma corrections, etc.
   * We should do this in a fragment shader so the user can adjust it with sliders.  There can also be a fast path for final adjustment where the processed textures are saved; however, to start adjusting again, we will need the source data.
* UTM projections.  I assume server-side.  What other projections?
* Show/hide layers based on viewer height(careful in 2D and Columbus view) or time?  This may be done in Dynamic Scene, not Scene, but we need to think about it.  More general _display conditions_ could also be useful.
* Ability to move - and possibility rotate - a texture on the globe so it better lines up with where the user expects it, e.g., with building models.  To start, we need to decouple the extent the texture thinks it has with the extent that it is rendered in.
* Blend maps for layers, e.g., specular, dirt, or destruction maps.  I don't have any use cases, but these are certainty popular in games; however, the shading for each layer is different, i.e., they are not just diffuse components.
* Fix blurriness in 2D and Columbus View when using Mercator imagery and a Mercator projection.  We'll probably do this by keeping the original Mercator images around for the first couple of levels.
* For better performance, we can minimize the complexity of fragment shading so only the most complex shading is done once.  Ignoring alpha, a layer can be seen as a diffuse map (which may need to go through a brightness filter given how dark some tiles are).  Instead of doing full lighting and atmosphere when rendering each tile, we can simply render the diffuse component, and then in a final pass, we can perform lighting with specular map, bump map, etc.
   * This is missing a lot of detail.
   * Of course, we could also lay down z first, but we might need the multi-frustum for that, and the CPU overhead could be too high.
* Determining what textures overlap what tiles can burn a lot of CPU.  An r-tree can be used to make this query fast (at the expense of creating and maintaining the tree, of course).  Perhaps there are already JavaScript r-tree implementations, or a simpler spatial data structure will suffice.  We also need to look at related r-tree patents to make sure we can use it.  Papers:
   * [R-Trees.  A Dynamic Index Structure for Spatial Searching](http://postgis.refractions.net/support/rtree.pdf).  1984.
   * [The R*-tree: An Efficient and Robust Access Method for  Points and Rectangles](http://infolab.usc.edu/csci587/Fall2011/papers/p322-beckmann.pdf).  1990.
   * [Priority r-tree](http://www.cse.ust.hk/~yike/prtree/).  2004.
* If a texture is completely occluded by opaque layers higher in the z-order, it does not need to be rendered.  Actually, it doesn't need to be requested from the server.  Hmm - could a proxy server do some compositing for us?
* `ArcGisMapServerImageryProvider`:
   * Read the extent and maybe tiling scheme from non-tiled services, instead of assuming global extent and geographic projection.
   * Support non-default. non-worldwide tiling schemes for tiled services.  http://webhelp.esri.com/arcgisserver/9.3/java/index.htm#what_is_map_caching.htm


## Other APIs with Layers
   * Insight3D - [Imagery Overlay](http://www.agi.com/resources/help/online/AGIComponents/Programmer's%20Guide/Overview/Graphics/GlobeOverlays/Imagery.html) and [Web Imagery Overlays](http://www.agi.com/resources/help/online/AGIComponents/Programmer's%20Guide/Overview/Graphics/GlobeOverlays/WebImagery.html).
   * OpenWebGlobe - [Tutorial](http://wiki.openwebglobe.org/doku.php?id=tutorial:webgl0103) and [reference](http://wiki.openwebglobe.org/doku.php?id=reference).
   * WebGL Earth - See `WebGLEarth.Map` in the [API](http://www.webglearth.org/api).
   * ReadyMap - [Layers demo](http://demo.pelicanmapping.com/rmweb/webgl/tests/twolayers.html).
   * Glob3 - [Layers example](http://ami.dis.ulpgc.es/glob3m/index.php?id=4&example=layers).
   * OpenLayers - [doc](http://docs.openlayers.org/library/layers.html); [reference doc](http://dev.openlayers.org/releases/OpenLayers-2.11/doc/apidocs/files/OpenLayers/Layer-js.html); and lots of [examples](http://openlayers.org/dev/examples/) such as [layer opacity](http://openlayers.org/dev/examples/layer-opacity.html).
   * Leaflet - [doc](http://leaflet.cloudmade.com/reference.html) and [examples](http://leaflet.cloudmade.com/examples.html).
   * ArcGIS - See _Layer_ in the [doc](http://help.arcgis.com/en/webapi/javascript/arcgis/help/jsapi_start.htm) and [samples](http://help.arcgis.com/en/webapi/javascript/arcgis/help/jssamples_start.htm).