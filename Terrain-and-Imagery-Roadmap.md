Cesium already has excellent support for streaming terrain and imagery, but there are lots of ways we can improve it.  This page catalogs the many possibilities.  Have ideas or want to get involved?  Introduce yourself on the [development mailing list](https://groups.google.com/d/forum/cesium-dev).

# Rendering

* Use multiple passes to successfully render tiles even if the number of textures exceeds the number of texture units supported by the WebGL stack (minimum: 8). May also need to render in multiple passes if we use too many uniforms.
  * Use blending in the render state to support layer alpha.

# Culling

* Improve computation of the "occludee point" used for horizon culling. It currently uses a sphere based on the ellipsoid's minimum radius, which is conservative, but using the actual ellipsoid will allow more tiles to be culled.

# Interaction with other primitives

# Loading

# Additional Data Sources

* Imagery
  * [Web Map Tile Service (WMTS)](http://www.opengeospatial.org/standards/wmts)
  * [ArcGIS ImageServer](http://resources.arcgis.com/en/help/rest/apiref/index.html?imageserver.html)
  * [VR-TheWorld](http://vr-theworld.com/)
* Terrain
  * [ArcGIS MapServer](http://resources.arcgis.com/en/help/rest/apiref/index.html?mapserver.html)

# Credits and Logos

* Avoid duplicate credits/logos when two layers from the same provider are shown, or if two providers have identical credits.
* 