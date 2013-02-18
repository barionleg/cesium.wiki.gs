Cesium already has excellent support for streaming terrain and imagery, but there are lots of ways we can improve it.  This page catalogs the many possibilities.  Have ideas or want to get involved?  Introduce yourself on the [development mailing list](https://groups.google.com/d/forum/cesium-dev).

# Ideas and Plans

## Rendering

* [ ] Use multiple passes to successfully render tiles even if the number of textures exceeds the number of texture units supported by the WebGL stack (minimum: 8). May also need to render in multiple passes if we use too many uniforms.
  * Use blending in the render state to support layer alpha.
* [ ] Sort tiles using the natural ordering of a quadtree rather than explicitly sorting tiles by distance.
* [ ] For better performance, we can minimize the complexity of fragment shading so only the most complex shading is done once. Ignoring alpha, a layer can be seen as a diffuse map (which may need to go through a brightness filter given how dark some tiles are). Instead of doing full lighting and atmosphere when rendering each tile, we can simply render the diffuse component, and then in a final pass, we can perform lighting with specular map, bump map, etc.
  * This is missing a lot of detail.
  * Of course, we could also lay down z first, but the CPU overhead could be too high.
* [ ] Shade surface with ambient occlusion, either precomputed and stored with terrain data or computed in screen space on the fly.
* [ ] Interesting ways to morph terrain during transitions between 2D, 3D, and Columbus View?
* [ ] Show terrain in 2D by bump mapping.
* [ ] Minimize popping artifacts by morphing between terrain LODs.
* [ ] Do per-pixel imagery LOD selection, blending between adjacent LODs.  This should drastically reduce hard lines between LODs when the imagery provider has a very different appearance at different LODs.
* [ ] Does lazying down Z first improve performance?  Horizon views only?  Is walking the tree in front-to-back order enough?
* [ ] Terrain tile selection in Columbus View does not closely match 3D.  For example, it's hard to get the most detailed version of Mt. Everest in Columbus View.

## Culling

* [ ] Improve computation of the "occludee point" used for horizon culling. It currently uses a sphere based on the ellipsoid's minimum radius, which is conservative, but using the actual ellipsoid will allow more tiles to be culled.  Also, it currently ignores terrain. These two wrongs seem to cancel each other out well enough that I've never seen artifacts from it, but the horizon culling is probably not optimal.
* [ ] Frustum cull more accurately than with a tile bounding sphere.  Bounding spheres don't fit tiles very tightly.  Some ideas here: http://outerra.blogspot.com/2012/11/view-frustum-culling-of-sphere-mapped.html
* [ ] Don't compute 2D bounding spheres every frame.

## Interaction with other parts of Cesium

* [ ] Layer primitives on the ground - at least polylines and polygons - seamlessly with imagery. Many people think in terms of vector layers, KML layers, etc. Everything is a layer. We should support this, but shouldn't lose sight of our focus on air and space where this paradigm breaks down.
* How should billboards interact with terrain?  We generally expect them to be get hidden behind hills, but when their bottoms get clipped off because they're below terrain it looks like a bug.
* Avoid duplicate credits/logos when two layers from the same provider are shown, or if two providers have identical credits.
* Show/hide layers based on viewer height(careful in 2D and Columbus view) or time? This may be done in Dynamic Scene, not Scene, but we need to think about it. More general display conditions could also be useful.
* Ability to move - and possibility rotate - a texture on the globe so it better lines up with where the user expects it, e.g., with building models. To start, we need to decouple the extent the texture thinks it has with the extent that it is rendered in.
* Add support for programmatic height queries.
   * Pick on terrain and get exact position.
   * Query height at point.  Get back exact height or height according to currently rendered LOD?
   * Notifications when LOD under a point switches, so the point can be kept on terrain?
* Render polygons on terrain - probably using shadow volumes
* Render polylines on terrain - perhaps see if we can use our [SIGGRAPH work](http://blogs.agi.com/agi/2011/04/25/a-screen-space-approach-to-rendering-polylines-on-terrain/) without a geometry shader.

## Loading

* Support skipping intermediate tiles in the tile pyramid.  For example, if the camera starts zoomed into, we should be able to load the high-res tiles immediately rather than refining down through the tree first and waiting at each level for the previous level to complete.
* Combine multiple images from the same layer into a single texture at load time.  This should substantially improve performance.
* Consider baking _multiple layers_ into a single texture per geometry tile. The downside to this is that it will be a performance hit when adjusting layer order, alpha, gamma, etc.
* Handle other projections?  UTM?
* Many APIs can restrict the zoom level. I assume it's useful - it's certainty trivial to expose in our code - but I'm not sure of the use cases. Performance?
* Fix blurriness in 2D and Columbus View when using Mercator imagery and a Mercator projection. We'll probably do this by keeping the original Mercator images around for the first couple of levels.  Currently we do a round-trip from Mercator->Geographic->Mercator.
* If a texture is completely occluded by opaque layers higher in the z-order, it does not need to be rendered. Actually, it doesn't need to be requested from the server. Hmm - could a proxy server do some compositing for us?
* Add a callback or some other way to learn that level 0 terrain/imagery is done loading.
* Upsample `TerrainMesh` instead of `TerrainData`? This could yield better performance, but at a memory cost because the mesh is bigger than the raw data, at least for heightmap terrain.
* Allow upsampling across more than one level at a time. This (may?) be necessary to skip levels when refining.
* More efficiently encode terrain data for transmission:
  * Use the Google Body techniques, encoding the mesh as a UTF-8 string: http://code.google.com/p/webgl-loader/wiki/BenCompressionStats
  * Encode each tile as a delta from its parent:
    * Parent tile indicates which of its vertices are in which quadrant with index ranges.
    * Child has new vertices, index list linking parent and child vertices into triangles, and new index ranges describing the division of its vertices among its child quadrants.
* When we've exceeded the actual terrain detail available, generate it procedurally using, for example, fractional Brownian motion: http://design.osu.edu/carlson/history/PDFs/p371-fournier.pdf
* When upsampling terrain by subsetting it, can we avoid copying heights to a separate TypedArray and instead pass a range to the `HeightmapTessellator`?  The Web Worker will copy the whole thing anyway, so this may or may not be worthwhile.

## Data Sources

* New imagery providers
  * [Web Map Tile Service (WMTS)](http://www.opengeospatial.org/standards/wmts)
  * [ArcGIS ImageServer](http://resources.arcgis.com/en/help/rest/apiref/index.html?imageserver.html)
  * [VR-TheWorld](http://vr-theworld.com/)
* New terrain providers
  * [ArcGIS MapServer](http://resources.arcgis.com/en/help/rest/apiref/index.html?mapserver.html)
* Improvements to existing providers
  * `ArcGisMapServerImageryProvider`
    * Read the extent and maybe tiling scheme from non-tiled services, instead of assuming global extent and geographic projection.
    * Support non-default, non-worldwide tiling schemes for tiled services. http://webhelp.esri.com/arcgisserver/9.3/java/index.htm#what_is_map_caching.htm

## Additional types of layers and effects

* Do we need layers for night lights? Why not layer a day image over night? In general, we need to revisit the architecture for night, bump, specular, clouds, etc. Clouds may happen sooner rather than later.
* Image processing to fix images, e.g.,
  * Bing Maps imagery is really dark, so brighten it. (done)
  * Landsat imagery is usually 11 or 12 bits, and loses its dynamic range when dropped to 8-bits.
  * For Landsat multispectral imagery, we might want to color one band.
  * Histogram, gamma corrections (done), etc.
  * We should do this in a fragment shader so the user can adjust it with sliders.
  * There can also be a fast path for final adjustment where the processed textures are saved; however, to start adjusting again, we will need the source data.
* Show/hide layers based on viewer height(careful in 2D and Columbus view) or time? This may be done in Dynamic Scene, not Scene, but we need to think about it. More general display conditions could also be useful.
* Blend maps for layers, e.g., specular, dirt, or destruction maps. I don't have any use cases, but these are certainty popular in games; however, the shading for each layer is different, i.e., they are not just diffuse components.
* Add support for tiled normal maps.
* Procedural shading by height, slope, etc.

# Resources

## Other APIs with Layers

   * Insight3D - [Imagery Overlay](http://www.agi.com/resources/help/online/AGIComponents/Programmer's%20Guide/Overview/Graphics/GlobeOverlays/Imagery.html) and [Web Imagery Overlays](http://www.agi.com/resources/help/online/AGIComponents/Programmer's%20Guide/Overview/Graphics/GlobeOverlays/WebImagery.html).
   * OpenWebGlobe - [Tutorial](http://wiki.openwebglobe.org/doku.php?id=tutorial:webgl0103) and [reference](http://wiki.openwebglobe.org/doku.php?id=reference).
   * WebGL Earth - See `WebGLEarth.Map` in the [API](http://www.webglearth.org/api).
   * ReadyMap - [Layers demo](http://demo.pelicanmapping.com/rmweb/webgl/tests/twolayers.html).
   * Glob3 - [Layers example](http://ami.dis.ulpgc.es/glob3m/index.php?id=4&example=layers).
   * OpenLayers - [doc](http://docs.openlayers.org/library/layers.html); [reference doc](http://dev.openlayers.org/releases/OpenLayers-2.11/doc/apidocs/files/OpenLayers/Layer-js.html); and lots of [examples](http://openlayers.org/dev/examples/) such as [layer opacity](http://openlayers.org/dev/examples/layer-opacity.html).
   * Leaflet - [doc](http://leaflet.cloudmade.com/reference.html) and [examples](http://leaflet.cloudmade.com/examples.html).
   * ArcGIS - See _Layer_ in the [doc](http://help.arcgis.com/en/webapi/javascript/arcgis/help/jsapi_start.htm) and [samples](http://help.arcgis.com/en/webapi/javascript/arcgis/help/jssamples_start.htm).

## Sources of data

* Terrain
  * [National Elevation Dataset](http://ned.usgs.gov/) - High quality terrain data for the conterminous United States, Alaska, Hawaii, and territorial islands.  Resolution as high as 3 meters for parts of the U.S.
  * [ASTER Global Digital Elevation Map](http://asterweb.jpl.nasa.gov/gdem.asp) - 30m resolution data for most of the world.
  * [Shuttle Radar Topography Mission (SRTM)](http://www2.jpl.nasa.gov/srtm/) - 90m resolution data for most of the world.  There's also a nicely-processed version of available from [CGIAR-CSI](http://srtm.csi.cgiar.org/), but special permission is required to use this processed version commercially.

## Papers

In addition to the [work mentioned in our book](http://www.virtualglobebook.com/bibliography.html), these recent papers could be worth a read:

* [Interactive Editing of GigaSample Terrain Fields](http://wwwcg.in.tum.de/research/research/publications/2012/interactive-editing-of-gigasample-terrain-fields.html).  2012.  Uses GPU ray casting.  Compression part could be interesting.  Didn't look into what they are using CUDA for, but we don't want to rely on WebCL.
* [On-the-Fly Decompression and Rendering of Multiresolution Terrain](https://e-reports-ext.llnl.gov/pdf/371781.pdf).  2010.  Uses a geometry shader but still potentially useful.
* [Terrain Rendering with the Combination of Mesh Simplification and Displacement Mapping](http://www.cescg.org/CESCG-2010/papers/Zsolt_Feher_TRwMESHandDisp.pdf).  2010.  Sounds like combining low resolution mesh with higher resolution displacement maps, but I only read the abstract.
* [GPU-Aware Hybrid Terrain Rendering](http://wwwcg.in.tum.de/research/research/publications/2010/gpu-aware-hybrid-terrain-rendering.html).  2010.  Interesting work, but I'm not sure how to efficiently map GPU ray casting to an ellipsoid.
* [Rendering Large Terrains in Real-Time](http://www.cescg.org/CESCG-2007/papers/Maribor-Rupnik-Bojan.pdf).  2007.
* [C-BDAM - Compressed Batched Dynamic Adaptive Meshes for Terrain Rendering](http://www.crs4.it/vic/cgi-bin/bib-page.cgi?id='Gobbetti:2006:CCB').  2006.
* [Out-of-core terrain rendering with reparameterized textures](http://www.cescg.org/CESCG-2004/papers/64_HarabaszJoachim.pdf).  2004.  Could be interesting for improving texture quality on steep cliffs.