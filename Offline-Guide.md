By default, Cesium uses several external data sources which require internet access at runtime, though none of these dependencies are required.  This guide lists these external sources and how to configure Cesium to work in a fully offline (no internet access) environment.

### Imagery

The default imagery provider in Cesium is Bing Maps.  This provider loads data from `dev.virtualearth.net` as well as several other tile servers that are subdomains of `virtualearth.net`.  To use another provider, pass it into the constructor for the `Viewer` widget.  

If you have an imagery server on your local network (e.g. WMS, ArcGIS, Google Earth Enterprise), you can configure Cesium to use that.  Otherwise, Cesium ships with a low-resolution set of images from Natural Earth II in `Assets/Textures/NaturalEarthII`, or you can download a higher-resolution tileset from the [cesium-assets](https://github.com/AnalyticalGraphicsInc/cesium-assets) repository.

By default, the `BaseLayerPicker` includes options for several sample online imagery and terrain sources.  In an offline application, you should either disable that widget completely, by passing `baseLayerPicker : false` to the `Viewer` widget, or use the `imageryProviderViewModels` and `terrainProviderViewModels` options to configure the sources that will be available in your offline application.

### Geocoder

The `Geocoder` widget, which allows flying to addresses and landmarks, uses the Bing Maps Locations API at `dev.virtualearth.net`.  In your offline application, you should disable this functionality by passing `geocoder : false` to the `Viewer` constructor.

### InfoBox

When you use `viewerDynamicObjectMixin`, selecting an object in the scene displays an HTML panel with information about that object.  HTML in the panel is sanitized to avoid [XSS](http://en.wikipedia.org/wiki/Cross-site_scripting) injections from untrusted data sources.  By default, Cesium loads the [Google Caja sanitizer](https://code.google.com/p/google-caja/) script from `caja.appspot.com` and uses that to sanitize HTML.  

In your offline application, you can [download the script](//caja.appspot.com/html-css-sanitizer-minified.js) locally, add it to your page, and configure Cesium to use that version by setting the `InfoBoxViewModel.defaultSanitizer` property.  See the example below.

### Example

This example shows how to configure Cesium to avoid use of online data sources.

```javascript
// assuming the Google Caja script has been loaded globally in your page
Cesium.InfoBoxViewModel.defaultSanitizer = html_sanitize;

var viewer = new Cesium.Viewer('cesiumContainer', {
  imageryProvider : new Cesium.TileMapServiceImageryProvider({
    url : 'Assets/Textures/NaturalEarthII'
  }),
  baseLayerPicker : false,
  geocoder : false
});
```