When you fire up Cesium for the first time, the first thing you probably notice is the high-resolution imagery data.  As you zoom closer, however, you notice that the Earth is just a smooth spheroid.  Where's the terrain?

High quality terrain visualization dramatically increases the realism of a virtual globe.  For that reason, it is one of our highest priorities to bring high-resolution, streaming, world-wide terrain to Cesium.

Fortunately, large-scale terrain rendering is a well-researched problem.  It still, however, presents a number of significant engineering challenges, some of which are described on this page.  

This is an area that has plenty of opportunities for interested folks to get involved and contribute.  If that's you, please introduce yourself on the [development mailing list](https://groups.google.com/d/forum/cesium-dev).

## Data sources

High-resolution, world-wide terrain datasets are enormous, from tens of gigabytes to tens of terabytes.  They need to be organized into a form suitable for visualization, and ideally be hosted on fast, geographically-distributed servers.  For Cesium to use a terrain data source out-of-the-box, that terrain data source should ideally be freely-accessible, at least for non-commercial use.  What are our options?

### ESRI World Elevation Services

http://www.arcgis.com/home/item.html?id=d3742572150f4fb5b22739fe94dea260

Advantages:
* Free for non-commercial use.  No additional charge for many organizations that already have ESRI licenses.
* Covers most of the world.
* Very high-resolution data for many parts of the world.
* Server can reproject to WGS84 geographic projection with ellipsoid-referenced heights, so little processing on the client will be required.
* Should be accessible via CORS once they upgrade to ArcGIS Server 10.1.

Disadvantages:
* Currently in Beta.
* Limited to downloading 1 billion pixels of terrain data per day.
* Accurate heights seem to be available only in TIFF format.  So we need a proxy to convert the data to a format readable by web browsers.

### VR-TheWorld

http://www.vr-theworld.com/

Advantages:
* A rack-mounted server with all data is available for sale, making it easy to host terrain data on a private network or incorporate your own terrain data.
* Terrain data uses a WGS84 geographic projection.
* Built on open standards like Web Mapping Service - Cached (WMS-C) and Tile Map Service (TMS).

Disadvantages:
* VERY tiny terrain tiles - 32x32 pixels.  Our client will need to request hundreds of tiles to render a scene.
* License terms for our use-case are unclear.
* Only serves data in TIFF format?

### Build our own public terrain server

Perhaps we could build and host our own terrain data set.  There is an abundance of freely-available terrain data available.  Here are some of the larger ones:
* [National Elevation Dataset](http://ned.usgs.gov/) - High quality terrain data for the conterminous United States, Alaska, Hawaii, and territorial islands.  Resolution as high as 3 meters for parts of the U.S.
* [ASTER Global Digital Elevation Map](http://asterweb.jpl.nasa.gov/gdem.asp) - 30m resolution data for most of the world.
* [Shuttle Radar Topography Mission (SRTM)](http://www2.jpl.nasa.gov/srtm/) - 90m resolution data for most of the world.  There's also a nicely-processed version of available from [CGIAR-CSI](http://srtm.csi.cgiar.org/), but special permission is required to use this processed version commercially.

Advantages:
* Full control over the organization of the data, so it can be optimized for our client.
* Ability to precompute metadata about terrain tiles, such as their geometric error, that can be used to ensure we're rendering very accurate scenes.

Disadvantages:
* Even though some data sets are public domain, it's difficult to obtain them in their entirety due to their size.  Probably need to make the right connections at the organizations that maintain these data sets.
* Hosting fees might get expensive.  Who pays?
* Significant work to process the terrain data to a common projection/datum, fill voids, etc.

### Private terrain servers

One option is to implement support for standard protocols like WMS and TMS (for example, with terrain servers like [Geoserver](http://geoserver.org)) and leave acquiring the actual terrain data as an "exercise for the reader."  For example, individual Cesium integrators could populate a private terrain server with DTED data or other data specific to their use-cases, and render that in Cesium.

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

## Architecture

This section is a work in progress, even more so than the rest of this page!

#### CentralBody

* Primarily responsible for the rendering of terrain and imagery.  Delegates various parts of the process to other types listed here.

#### TilingScheme

* Defines the shape of the quadtree.  For example, tiles may be web-mercator-aligned or geographic/WGS84 aligned.
* Creates quadtree tiles on demand.
* Transforms tile coordinates (x, y, level) to world extent.

#### GeometryProvider

* Async-oriented, loading is throttled.
* Creates geometry for a given tile by tessellating an ellipsoid or height map, or by downloading a mesh.  Fills in the Tile provided to it.  Texture coordinates are included in the mesh.
* Has a TilingScheme.

#### Tile

* A node in the quadtree.
* Has tile coordinates, x, y, and level.
* Defines the geometric shape of the terrain surface using a mesh or vertex array, plus a "center" for RTC rendering.
* Knows its bounding volume (sphere?), occludee point for horizon culling, and geometric error.
* Doesn't _do_ anything, really.  Just holds data.

#### ImageryProvider

* Async-oriented, loading is throttled.
* Fills in the texture and texture matrix on the Tile provided to it.

#### ImageryLayer

#### TileImagery

* The imagery associated with a single tile.
* Knows its load pipeline state, load fail count, etc.
* Represents exactly one texture and one texture matrix.

### Process of creating new tiles

The code that does this probably lives in `CentralBody`.

1. Ask `TilingScheme` to create new tile(s).  They are initially empty.
2. Ask `GeometryProvider` to fill each tile with the tile mesh, bounding volume, geometric error, etc.  This happens asynchronously.
3. Ask each `ImageryProvider` to fill each tile with a texture representing this tile's imagery from the imagery provider.  This happens asynchronously.

To be decided: When terrain and imagery tiles are not aligned, is each imagery tile that applies to a terrain tile a separate texture with a separate texture matrix?  Or do we render tiles to a FBO attached to a texture that _is_ aligned with the terrain tile?

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