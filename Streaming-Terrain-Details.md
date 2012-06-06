Design and implementation ideas for streaming imagery.

* Stream world terrain from servers like [Esri](http://resources.arcgis.com/content/imagery/10.0/world_elevation).
* Stream (converted) DTED files via [Geoserver](http://geoserver.org).

* Client-side (approximate) level-of-detail control.
* Show terrain in Columbus view.
* Interesting ways to morph terrain during transitions?
* 2D - turn on?  or use for bump mapping?

## Medium term

* Host terrain on the amazon cloud?  Or [Storm](http://www.stormondemand.com/) for its SSDs?

## Longer term

* Does laying down z first improve performance?  Horizon views only?  Is walking the tree in front-to-back order enough?
* Procedural shading by height, slope, etc.

### Vector Data

* Polygons on terrain - probably shadow volumes
* Polylines on terrain - perhaps see if we can use our [SIGGRAPH work](http://blogs.agi.com/agi/2011/04/25/a-screen-space-approach-to-rendering-polylines-on-terrain/) without a geometry shader.
* Billboards that do not partially sink under terrain.