# heightmap-1.0 terrain format

This file exists for historical reasons.  This format is deprecated and should not be used.  Consider [quantized-mesh](https://github.com/AnalyticalGraphicsInc/quantized-mesh) instead.

A terrain tileset in `heightmap-1.0` format is simple multi-resolution quadtree pyramid of heightmaps according to the [Tile Map Service (TMS)](http://wiki.osgeo.org/wiki/Tile_Map_Service_Specification) layout and global-geodetic profile. All tiles have the extension `.terrain`. So, if the Tiles URL for a tileset is:

```
http://cesiumjs.org/tilesets/terrain/smallterrain
```

Then the two root files of the pyramid are found at these URLs:

* (-180 deg, -90 deg) - (0 deg, 90 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/0/0/0.terrain
* (0 deg, -90 deg) - (180 deg, 90 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/0/1/0.terrain

The eight tiles at the next level are found at these URLs:

* (-180 deg, -90 deg) - (-90 deg, 0 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/0/0.terrain
* (-90 deg, -90 deg) - (0 deg, 0 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/1/0.terrain
* (0 deg, -90 deg) - (90 deg, 0 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/2/0.terrain
* (90 deg, -90 deg) - (180 deg, 0 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/3/0.terrain
* (-180 deg, 0 deg) - (-90 deg, 90 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/0/1.terrain
* (-90 deg, 0 deg) - (0 deg, 90 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/1/1.terrain
* (0 deg, 0 deg) - (90 deg, 90 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/2/1.terrain
* (90 deg, 0 deg) - (180 deg, 90 deg) - http://cesiumjs.org/tilesets/terrain/smallterrain/1/3/1.terrain

The tiles are 65x65 vertices and overlap their neighbors at their edges. In other words, at the root, the eastern-most column of heights in the western tile is identical to the western-most column of heights in the eastern tile.

Terrain tiles are served gzipped. Once extracted, they are at least 8,452 bytes in size. The first and most important part of the file is a simple array of 16-bit, little-endian, integer heights arranged from north to south and from west to east - the first 2 bytes are the height in the northwest corner, and the next 2 bytes are the height at the location just to the east of there. Each height is the number of 1/5 meter units above -1000 meters. The total size of the post data is `65 * 65 * 2 = 8450` bytes.

Following the height data is one additional byte which is a bit mask indicating which child tiles are present. The bit values are as follows:

* Southwest - bit 0 - value 1
* Southeast - bit 1 - value 2
* Northwest - bit 2 - value 4
* Northeast - bit 3 - value 8

If a bit is set, the corresponding `.terrain` file can be expected to be found on the server as well. If it is cleared, requesting the `.terrain` file will return a 404 error.

The child bit mask is followed by the water mask. The water mask is either 1 byte, in the case that the tile is all land or all water, or it is `256 * 256 * 1 = 65536` bytes if the tile has a mix of land and water. Each mask value is 0 for land and 255 for water. Values between 0 and 255 are allowed as well (but not currently present in the data) in order to support anti-aliasing of the coastline.
