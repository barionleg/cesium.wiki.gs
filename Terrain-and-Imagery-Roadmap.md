Cesium already has excellent support for streaming terrain and imagery, but there are lots of ways we can improve it.  This page catalogs the many possibilities.  Have ideas or want to get involved?  Introduce yourself on the [development mailing list](https://groups.google.com/d/forum/cesium-dev).

# Rendering

* Use multiple passes to successfully render tiles even if the number of textures exceeds the number of texture units supported by the WebGL stack (minimum: 8). May also need to render in multiple passes if we use too many uniforms.
  * Use blending in the render state to support layer alpha.
* Sort tiles using the natural ordering of a quadtree rather than explicitly sorting tiles by distance.


# Culling

* Improve computation of the "occludee point" used for horizon culling. It currently uses a sphere based on the ellipsoid's minimum radius, which is conservative, but using the actual ellipsoid will allow more tiles to be culled.

# Interaction with other primitives

* Layer primitives on the ground - at least polylines and polygons - seamlessly with imagery. Many people think in terms of vector layers, KML layers, etc. Everything is a layer. We should support this, but shouldn't lose sight of our focus on air and space where this paradigm breaks down.
* How should billboards interact with terrain?  We generally expect them to be get hidden behind hills, but when their bottoms get clipped off because they're below terrain it looks like a bug.


# Loading

* Combine multiple images from the same layer into a single texture at load time.  This should substantially improve performance.
* Consider baking _multiple layers_ into a single texture per geometry tile. The downside to this is that it will be a performance hit when adjusting layer order, alpha, gamma, etc.
* 

# Additional Data Sources

* Imagery
  * [Web Map Tile Service (WMTS)](http://www.opengeospatial.org/standards/wmts)
  * [ArcGIS ImageServer](http://resources.arcgis.com/en/help/rest/apiref/index.html?imageserver.html)
  * [VR-TheWorld](http://vr-theworld.com/)
* Terrain
  * [ArcGIS MapServer](http://resources.arcgis.com/en/help/rest/apiref/index.html?mapserver.html)

# Additional types of layers and effects

* Do we need layers for night lights? Why not layer a day image over night? In general, we need to revisit the architecture for night, bump, specular, clouds, etc. Clouds may happen sooner rather than later.
* Image processing to fix images, e.g.,
  * Bing Maps imagery is really dark, so brighten it.
  * Landsat imagery is usually 11 or 12 bits, and loses its dynamic range when dropped to 8-bits.
  * For Landsat multispectral imagery, we might want to color one band.
  * Histogram, gamma corrections, etc.
  * We should do this in a fragment shader so the user can adjust it with sliders. There can also be a fast path for final adjustment where the processed textures are saved; however, to start adjusting again, we will need the source data.

# Credits and Logos

* Avoid duplicate credits/logos when two layers from the same provider are shown, or if two providers have identical credits.

# Random ideas in need of a use case

* Many APIs can restrict the zoom level. I assume it's useful - it's certainty trivial to expose in our code - but I'm not sure of the use cases. Performance?