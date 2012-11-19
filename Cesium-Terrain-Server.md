# Cesium Terrain Server

This page describes the format and layout of the terrain data hosted at:
http://cesium.agi.com/terrain/

> Note: the above URL will return "403 - Forbidden" because browsing is not supported.

The terrain server is still very much a work in progress, so the format can and will change in the future.

The server currently hosts a mosaic of [GTOPO30](http://eros.usgs.gov/#/Find_Data/Products_and_Data_Available/gtopo30_info) and [CGIAR SRTM](http://srtm.csi.cgiar.org/) terrain data.  SRTM is used from -60 degrees to 60 degrees latitude and all longitudes.  GTOPO30 is used north of 60 degrees latitude and south of -60 degrees latitude.  Additional sources, including high-resolution NED terrain, will be added in the future.

The data are organized into a simple multi-resolution pyramid of heightmaps according to the [Tile Map Service (TMS)](http://wiki.osgeo.org/wiki/Tile_Map_Service_Specification) layout and the global-geodetic profile.  All tiles have the extension `.terrain`.  So, the two root tiles are found at these URLs:

http://cesium.agi.com/terrain/0/0/0.terrain
http://cesium.agi.com/terrain/0/1/0.terrain

