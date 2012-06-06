Design and implementation ideas for streaming imagery.

* Stream world terrain from servers like [Esri](http://resources.arcgis.com/content/imagery/10.0/world_elevation).
* Stream (converted) DTED files using [Geoserver](http://geoserver.org) via WMS.

* Client-side (approximate) level-of-detail control.
* Show terrain in Columbus view.
* Interesting ways to morph terrain during transitions?
* 2D - what happens to terrain?  Bump mapping?
* Rendering
   * Fill cracks between tiles.  How can our screen-space work for ellipsoid tiles be adapted?  Plan B - skirts.
   * Popping artifacts.  Morph between LODs?  Do nothing?

## Medium term

* Host terrain on the amazon cloud?  Or [Storm](http://www.stormondemand.com/) for its SSDs?

## Longer term

* Pick on terrain and get exact position - not dependent on terrain LOD.
* Does laying down z first improve performance?  Horizon views only?  Is walking the tree in front-to-back order enough?
* Procedural shading by height, slope, etc.

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