CesiumJS is built with care; code is publicly peer-reviewed, is unit tested with over 90% code coverage, and is statically analyzed, documented, and developed by an experienced team.

## Dynamic Geospatial Visualization
- Use [3D Tiles](sandcastle.cesium.com/index.html?src=3D%20Tiles%20Photogrammetry&label=3D%20Tiles) to stream, style, and interact with heterogeneous 3D data, including photogrammetry models, 3D buildings, CAD and BIM exterior and interiors, and point clouds.
  - [Style point clouds](https://sandcastle.cesium.com/index.html/?src=3D%20Tiles%20Point%20Cloud%20Shading.html) with size attenuation and Eye-Dome Lighting.
  - Classify [3D tilesets](https://sandcastle.cesium.com/index.html/?src=3D%20Tiles%20Photogrammetry%20Classification.html) or [terrain](https://sandcastle.cesium.com/index.html/?src=3D%20Tiles%20Terrain%20Classification.html) with another 3D tileset or graphics primitive.  [Invert classification](https://sandcastle.cesium.com/index.html/?src=Classification.html)
  - Optimize streaming performance with [Google Draco](https://cesium.com/blog/2018/04/09/draco-compression/) mesh and point cloud compression.
- Visualize high-resolution global [terrain](https://sandcastle.cesium.com/index.html/?src=Terrain.html). Optionally [exaggerate terrain](https://sandcastle.cesium.com/index.html/?src=Terrain%20Exaggeration.html). Apply [procedural materials](https://sandcastle.cesium.com/index.html/?src=Globe%20Materials.html) such as height- or slope-based color ramps.
- [Layer imagery](https://sandcastle.cesium.com/index.html/?src=Imagery%20Layers.html) from multiple sources, including WMS, TMS, WMTS with [time-dynamic imagery](https://sandcastle.cesium.com/index.html/?src=Web%20Map%20Tile%20Service%20with%20Time.html), Cesium ion, Bing Maps, Mapbox, GEE, OpenStreetMap, ArcGIS MapServer, standard image files, and custom tiling schemes. Each layer can be alpha-blended with the layers below it, and its brightness, contrast, gamma, hue, and saturation can be dynamically changed. Two layers can be [split across the screen](https://sandcastle.cesium.com/index.html/?src=Imagery%20Layers%20Split.html).
- Stream terrain, imagery, 3D Tiles, and glTF assets from [Cesium ion](https://sandcastle.cesium.com/index.html/?src=Sentinel-2.html&amp;label=ion%20Assets).
- Use legacy Google Earth Enterprise [terrain and imagery](https://sandcastle.cesium.com/index.html/?src=Google%20Earth%20Enterprise.html)
- Industry standard vector formats, such as [KML](https://sandcastle.cesium.com/index.html/?src=KML.html&amp;label=DataSources), [GeoJSON and TopoJSON](https://sandcastle.cesium.com/index.html/?src=GeoJSON%20and%20TopoJSON.html&amp;label=DataSources), including terrain clamping.
- Draw [3D models](https://sandcastle.cesium.com/index.html/?src=3D%20Models.html) using glTF 2.0 with Physically-Based Rendering (PBR) materials, animations, skins, and morph targets.  Clamp models to terrain and highlight their [silhouette](https://sandcastle.cesium.com/index.html/?src=3D%20Models%20Coloring.html). Use the binary glTF, Google Draco, and [WEB3D_quantized_attributes](https://github.com/KhronosGroup/glTF/blob/master/extensions/Vendor/WEB3D_quantized_attributes/README.md) extensions to reduce the file size.
- Create data-driven time-dynamic scenes using [CZML](https://sandcastle.cesium.com/index.html/?src=CZML.html) and stream massive amounts of time-dynamic data with [multi-part CZML](https://sandcastle.cesium.com/index.html/?src=Multi-part%20CZML.html).
- Draw and style a wide range of geometries:
  - [Polylines](https://sandcastle.cesium.com/index.html/?src=Polylines.html) and [dashed polylines](https://sandcastle.cesium.com/index.html/?src=Polyline%20Dash.html)
  - [Billboards](https://sandcastle.cesium.com/index.html/?src=Billboards.html)
  - [Labels](https://sandcastle.cesium.com/index.html/?src=Labels.html)
  - [Points](https://sandcastle.cesium.com/index.html/?src=Points.html)
  - Draw and extrude [polygons, polygons with holes](https://sandcastle.cesium.com/index.html/?src=Polygon.html&amp;label=Geometries), [rectangles](https://sandcastle.cesium.com/index.html/?src=Rectangle.html&amp;label=Geometries), [circles and ellipses](https://sandcastle.cesium.com/index.html/?src=Ellipse.html&amp;label=Geometries)
  - [Boxes](https://sandcastle.cesium.com/index.html/?src=Box.html&amp;label=Geometries), [cylinders](https://sandcastle.cesium.com/index.html/?src=Cylinder.html&amp;label=Geometries), [spheres and ellipsoids](https://sandcastle.cesium.com/index.html/?src=Ellipsoid.html&amp;label=Geometries)
  - [Corridors](https://sandcastle.cesium.com/index.html/?src=Corridor.html&amp;label=Geometries), [polyline volumes](https://sandcastle.cesium.com/index.html/?src=Polyline%20Volume.html&amp;label=Geometries), and [walls](https://sandcastle.cesium.com/index.html/?src=Wall.html&amp;label=Geometries)
- Clamp polylines, polygons, labels, billboards, and ground-based primitives [to the ground/terrain](https://sandcastle.cesium.com/index.html/?src=Clamp%20to%20Terrain.html).
- Layer and [z-order](https://sandcastle.cesium.com/index.html/?src=Z-Indexing%20Geometry.html) ground-based primitives.
- Create visual effects including:
  - [Shadows](https://sandcastle.cesium.com/index.html/?src=Shadows.html), including self-shadows and soft-shadows based on the sun position.
  - Atmosphere, fog, sun, sun lighting, moon, stars, and water.
  - [Particle system](https://sandcastle.cesium.com/index.html/?src=Particle%20System.html) effects such as smoke, fire, and sparks.
  - [Post-processing effects](https://sandcastle.cesium.com/index.html/?src=Ambient%20Occlusion.html&amp;label=Post%20Processing) including Ambient Occlusion, Bloom, Depth of Field, Silhouettes, and Lens Flare.  [Selectively apply](https://sandcastle.cesium.com/index.html/?src=Per-Feature%20Post%20Processing.html&amp;label=Post%20Processing) post-processing effects to individual primitives.  Create [custom post-processing effects](https://sandcastle.cesium.com/index.html/?src=Custom%20Post%20Process.html&amp;label=Post%20Processing) and pipelines of stages.
  - Fast Approximate Anti-aliasing (FXAA)
  - Efficient translucent primitives using [Order Independent Transparency](https://cesium.com/blog/2014/03/14/weighted-blended-order-independent-transparency/) (OIT).
- Apply clipping planes to [3D tilesets](https://sandcastle.cesium.com/index.html/?src=3D%20Tiles%20Clipping%20Planes.html), [terrain](https://sandcastle.cesium.com/index.html/?src=Terrain%20Clipping%20Planes.html, and 3D models.
- Individual object [picking](https://sandcastle.cesium.com/index.html/?src=Picking.html) and terrain picking.
- [Camera](https://sandcastle.cesium.com/index.html/?src=Camera.html) navigation with mouse and touch handlers for rotate, zoom, pan with inertia, flights, free look, and terrain collision detection.
- Batching, culling, and JavaScript and GPU optimizations for performance. Optimized to reduce CPU and power usage when not animating.
- Precision handling for large view distances ([logarithmic depth buffer and multiple frusta](https://cesium.com/blog/2018/05/24/logarithmic-depth/) to avoid z-fighting) and large world coordinates (emulated GPU double precision to avoid jitter
- A 3D globe, 2D map, and Columbus view (2.5D) with the same API. 3D views can use a [perspective or orthographic projection](https://sandcastle.cesium.com/index.html/?src=Projection.html).
- Display military symbology, such as MIL-STD-2525 and STANAG APP6, by [integrating with milsymbol](https://cesium.com/blog/2016/07/20/Cesium-and-milsymbol/).
- [Cluster](https://sandcastle.cesium.com/index.html/?src=Clustering.html) points, labels and billboards.

## Widgets
- Timeline and animation widgets for controlling simulation time.
- Base layer picker widget for selecting imagery and terrain.
- Selection and info box widgets for highlighting objects and displaying information.
- Geocoder widget for flying to addresses and landmarks using Cesium ion web services and [custom services](https://sandcastle.cesium.com/index.html/?src=Custom%20Geocoder.html).
- Home view widget to fly to the default camera view.
- Scene mode picker widget to morph between 3D, 2D, and Columbus view.
- Fullscreen widget for toggling fullscreen mode.
- Navigation help widget for providing mouse and touch instructions.
- Performance watch dog for monitoring the frame rate.
- [Inspector widget](https://sandcastle.cesium.com/index.html/?src=Cesium%20Inspector.html) for advanced graphics debugging.
- [WebVR widget](https://sandcastle.cesium.com/index.html/?src=Cardboard.html) for viewing Cesium with VR devices like Google Cardboard.

## High-Precision Math and Time
- Reference frames such as World Geodetic System (WGS84), International Celestial Reference Frame (ICRF), and east-north-up.
- Equidistant Cylindrical and Mercator 2D map projections.
- Conversions such as longitude/latitude/height to Cartesian.
- Fast Cartesian, spherical, cartographic, matrix, and quaternion types.
- Julian dates, leap seconds, and UTC and TAI time standards.

## Flexible Deployment
- Use Cesium as a single .js file (plus .css and web-workers .js files) or with Asynchronous Module Definition (AMD) to include only what you use.
- [Integrate with Webpack](https://cesium.com/blog/2017/10/18/cesium-and-webpack/)
- Create cross-platform desktop apps with [Cesium and Electron](https://cesium.com/blog/2016/04/04/Creating-Cesium-Desktop-Apps-with-Electron/).
- Create mobile apps with [Cesium and Cordova](https://cesium.com/blog/2016/05/18/An-Introduction-to-Cesium-Android-Apps-with-Cordova/)
