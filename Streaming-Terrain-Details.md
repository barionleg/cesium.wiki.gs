When you fire up Cesium for the first time, the first thing you probably notice is the high-resolution imagery data.  As you zoom closer, however, you notice that the Earth is just a smooth spheroid.  Where's the terrain?

High quality terrain visualization dramatically increases the realism of a virtual globe.  For that reason, it is one of our highest priorities to bring high-resolution, streaming, world-wide terrain to Cesium.

Fortunately, large-scale terrain rendering is a well-researched problem.  It still, however, presents a number of significant engineering challenges, some of which are described on this page.  

This is an area that has plenty of opportunities for interested folks to get involved and contribute.  If that's you, please introduce yourself on the [development mailing list](https://groups.google.com/d/forum/cesium-dev).

## To Do List

Streaming terrain implementation is currently taking place in the [imagery_layers](https://github.com/AnalyticalGraphicsInc/cesium/tree/imagery_layers) branch.  Here's our wildly-incomplete to-do list:

* _DONE_ Implement 2D and Columbus View.  They're currently completely broken.
* Fix Mercator projection 2D and Columbus View.
* Do we need to light the terrain/imagery?  We can do that by including normals in terrain vertex arrays or maybe by using a fancy technique like screen-space ambient occlusion.
* Check tile selection algorithm - is it rendering too much detail?
* Improve tile culling.
* Add support for switching terrain providers after rendering has started.
* Look more closely at the API - what happens when "public" properties are changed after construction?
* _DONE_ Fix black tiles at extreme zoom levels.  Handle failed imagery loads by using the parent tile's imagery.
* Allow imagery detail to increase independent of increasing terrain detail.
* _DONE_ Allow terrain detail to increase independent of increasing imagery detail.
* Support more textures per tile than are directly supported by the GPU.
* Set up a simple terrain server to host the default Cesium terrain.
* Set up a more sophisticated terrain server with better data, meshes instead of heightmaps, geometric error information, etc.
* Improve the replacement policy.  Currently it simply keeps the tiles that were used last frame, mostly.
* _DONE_ Make sure everything still works when there are multiple Cesium instances on a page.

## Data sources

Cesium supports the following source of terrain data:

### EllipsoidTerrainProvider

A very simple terrain provider that matches the WGS84 ellipsoid.  In other words, the terrain height is 0.0 for the entire world.

### ArcGisImageServerTerrainProvider

Provides elevation data downloaded as heightmaps from an [Esri ArcGIS ImageServer](http://www.esri.com/software/arcgis/serverimage).

This terrain provider can connect to any ArcGIS ImageServer.  However, the connection to the ImageServer must be proxied through the `/terrain/` service included with the Cesium Jetty-based web server, or an equivalent service.  This is because the full-resolution heights are only offered in TIF format, and because most browsers can't read TIF files.

The `/terrain/` proxy retrieves the TIF file from the ImageServer and then converts it to a specially-encoded, 24-bit PNG for transfer to the browser.  To produce the PNG, the proxy first adds 1000.0 meters to the height and then multiplies it by one thousand.  You can think of this as a height, in millimeters, above -1000.0 meters from the ellipsoid surface.  Then, the transformed height is encoded as a 24-bit integer where the red channel has the highest-order byte, the green channel has the middle-order byte, and the blue channel has the lowest-order byte.

Esri hosts such an ImageServer loaded with high-quality terrain data, and details can be found here:
http://www.arcgis.com/home/item.html?id=d3742572150f4fb5b22739fe94dea260

It is tempting to ship Cesium with this terrain source pointed at Esri's elevation service out-of-the-box, but we should avoid doing so for the following reasons:
* The service is in beta.
* We would have to pass on Esri's licensing requirements, which mandate that the service be used for non-commercial purposes or by Esri's existing customers.
* The elevation heightmaps are not cached on the server, so the response time from the server is not as high as we'd like.
* The proxy requirement, as described above, adds latency and complexity to the system.

### TileMapServiceTerrainProvider

Provides elevation data downloaded as heightmaps from a TileMapService (TMS) server.

Currently, this terrain provider assumes that the tiles use a geographic projection, it has 12 levels of detail, and that the heights are encoded in PNG files as described for the `/terrain/` service above.  There's lots of opportunity for generalization.

### WebMapServiceTerrainProvider

Provides elevation data downloaded as an array of heights from a Web Map Service (WMS) server via `XMLHttpRequest`.

Currently, this terrain provider assumes that the tiles use a geographic projection, it has 18 levels of detail, and that the heights are represented as a simple array of 16-bit integer heights, in meters.  If serving WMS via [GeoServer](http://geoserver.org), you will need to use the [DDS/BIL extension](http://docs.geoserver.org/stable/en/user/community/dds/index.html).  We also recommend that you use the [CORS Filter](http://software.dzhuvinov.com/cors-filter-installation.html) (or something similar) to allow your WMS server to be accessed from other domains.

This terrain provider needs a lot more work to be made applicable to a wider variety of WMS situations.

### Future terrain providers

* A terrain provider that downloads cached meshes, rather than heightmaps like the terrain providers above, using `XMLHttpRequest`.  In the future, we may provide a server that can be loaded with terrain data which is then converted to simplified meshes for efficient streaming to the client.

### Hosting our own terrain data

We want Cesium to have great terrain out of the box, and that means we need to host the terrain data ourselves.  Here are some potential sources of terrain data that we can use to populate our own terrain server:

* [National Elevation Dataset](http://ned.usgs.gov/) - High quality terrain data for the conterminous United States, Alaska, Hawaii, and territorial islands.  Resolution as high as 3 meters for parts of the U.S.
* [ASTER Global Digital Elevation Map](http://asterweb.jpl.nasa.gov/gdem.asp) - 30m resolution data for most of the world.
* [Shuttle Radar Topography Mission (SRTM)](http://www2.jpl.nasa.gov/srtm/) - 90m resolution data for most of the world.  There's also a nicely-processed version of available from [CGIAR-CSI](http://srtm.csi.cgiar.org/), but special permission is required to use this processed version commercially.

## Rendering ideas

* Client-side (approximate) level-of-detail control.
* Show terrain in Columbus view.
* Interesting ways to morph terrain during transitions?
* 2D - what happens to terrain?  Bump mapping?
* Rendering
   * Fill cracks between tiles.  How can our screen-space work for ellipsoid tiles be adapted?  Plan B - skirts.
   * Popping artifacts.  Morph between LODs?  Do nothing?

### Longer term

* Pick on terrain and get exact position - not dependent on terrain LOD.
* Does laying down z first improve performance?  Horizon views only?  Is walking the tree in front-to-back order enough?
* Procedural shading by height, slope, etc.
* Efficiently encode terrain data for transmission:
   * Use the Google Body techniques, encoding the mesh as a UTF-8 string: http://code.google.com/p/webgl-loader/wiki/BenCompressionStats
   * Encode each tile as a delta from its parent:
      * Parent tile indicates which of its vertices are in which quadrant with index ranges.
      * Child has new vertices, index list linking parent and child vertices into triangles, and new index ranges describing the division of its vertices among its child quadrants.

### Vector Data

* Polygons on terrain - probably shadow volumes
* Polylines on terrain - perhaps see if we can use our [SIGGRAPH work](http://blogs.agi.com/agi/2011/04/25/a-screen-space-approach-to-rendering-polylines-on-terrain/) without a geometry shader.
* Billboards that do not partially sink under terrain.

## Resources

* Lots of terrain LOD papers at [vterrain.org](http://vterrain.org/LOD/Papers/).  Also see their [Global Elevation Datasets](http://vterrain.org/Elevation/global.html).
* In addition to the [work mentioned in our book](http://www.virtualglobebook.com/bibliography.html), these recent papers could be worth a read:
   * [Interactive Editing of GigaSample Terrain Fields](http://wwwcg.in.tum.de/research/research/publications/2012/interactive-editing-of-gigasample-terrain-fields.html).  2012.  Uses GPU ray casting.  Compression part could be interesting.  Didn't look into what they are using CUDA for, but we don't want to rely on WebCL.
   * [On-the-Fly Decompression and Rendering of Multiresolution Terrain](https://e-reports-ext.llnl.gov/pdf/371781.pdf).  2010.  Uses a geometry shader but still potentially useful.
   * [Terrain Rendering with the Combination of Mesh Simplification and Displacement Mapping](http://www.cescg.org/CESCG-2010/papers/Zsolt_Feher_TRwMESHandDisp.pdf).  2010.  Sounds like combining low resolution mesh with higher resolution displacement maps, but I only read the abstract.
   * [GPU-Aware Hybrid Terrain Rendering](http://wwwcg.in.tum.de/research/research/publications/2010/gpu-aware-hybrid-terrain-rendering.html).  2010.  Interesting work, but I'm not sure how to efficiently map GPU ray casting to an ellipsoid.
   * [Rendering Large Terrains in Real-Time](http://www.cescg.org/CESCG-2007/papers/Maribor-Rupnik-Bojan.pdf).  2007.
   * [C-BDAM - Compressed Batched Dynamic Adaptive Meshes for Terrain Rendering](http://www.crs4.it/vic/cgi-bin/bib-page.cgi?id='Gobbetti:2006:CCB').  2006.
   * [Out-of-core terrain rendering with reparameterized textures](http://www.cescg.org/CESCG-2004/papers/64_HarabaszJoachim.pdf).  2004.  Could be interesting for improving texture quality on steep cliffs.