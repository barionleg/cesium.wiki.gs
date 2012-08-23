Design and implementation ideas for our screen-space rendering algorithms.

## Overview

* Scriptable like [Fabric](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Fabric).
* Chain together multiple filters to create an effect, e.g., bloom.
   * Create chains using other chains as building blocks (also like Fabric).
   * Pool or minimize intermediate textures.
* Full-screen or custom size.
* Tweak uniforms, e.g., brightness.
* Read from color and depth.
   * Name textures earlier in the pipeline and access them as input by name, e.g., a glow map or velocity buffer.
   * Read different resolutions?
* Render anywhere in the pipeline, not just at the end.
* A built-in set of common filters.

## Example Filter Scripts

Using a single built-in filter:
```json
{
  "type" : "brightness",
  "uniforms" : {
    "amount" : 1.2
  }
}
```

Creating a new filter:
```json
{
  "type" : "red",
  "source" : "czm_Filter czm_getFilter(czm_FilterInput filterInput) { czm_Filter f = agi_getDefaultFilter(filterInput); f.color = vec4(texture2D(filterInput.color, filterInput.st).r, 0.0, 0.0, 1.0); return f; }"
}
```

In GLSL, `czm_FilterInput` and `czm_Filter` are structs with the following definition:
```glsl
struct czm_FilterInput
{
  sampler2D color;
  vec2 colorStep; // 1.0 / (width, height)
  sampler2D depth;
  vec2 depthStep; // 1.0 / (width, height)
  vec2 st;
};

struct czm_Filter
{
  vec4 color;
}
```
All filters must implement the GLSL function, `czm_getFilter`.  The most trivial implementation, which just passes the input through, is:
```glsl
czm_Filter czm_getFilter(czm_FilterInput filterInput)
{
  return agi_getDefaultFilter(filterInput);
}
```
Here is another new filter, this time with uniforms:
```json
{
  "type" : "channels",
  "uniforms" : {
    "mask" : {
      r : 1.0,
      g : 1.0,
      b : 0.0,
      a : 1.0
    }
  }
  "source" : "czm_Filter czm_getFilter(czm_FilterInput filterInput) { czm_Filter f = agi_getDefaultFilter(filterInput); f.color = texture2D(filterInput.color, filterInput.st) * mask; return f; }"
}
```

## Example Filter Chain Scripts

Chaining together a Sobel edge detection filter and quantization to create a toon filter:
```json
{
  type : "toon",
  filters : {
    sobelPass : {
      "type" : "SobelEdgeDetect"
    },
    quantizePass : {
      "type" : "Quantize"
    }
  },
  chain : [
    "sobelPass",
    "quantizePass"
  ]
}
```

TODO: connect input and output?  Perhaps explicitly name them.
TODO: Need to explicitly name filters in a chain to access from several passes ago?

## Adding Filters to the Pipeline

TODO

## Built-in Filters

Color Buffer only
* Night vision.  ([simple algorithm](http://wtomandev.blogspot.com/2009/09/night-vision-effect.html).  Game Engine Gems 2, Chapter 3).
* Luminance (Graphics Shaders, Page 203.  Orange Book, Page 534)
* Brightness (Graphics Shaders, Page 233.  Orange Book, Page 537)
* Contrast (Graphics Shaders, Page 234.  Orange Book, Page 538)
* Hue Shifting (Graphics Shaders, Page 207)
* Edge Detection (Graphics Shaders, Page 220.  Orange Book, Page 552)
* Toon Shading (Graphics Shaders, Page 223)
* Gaussian Blur (RTR, Page 468.  Graphics Shaders, Page 210.  Orange Book, Page 549)
* Bloom (GPU Pro, Page 551.  GPU Pro 2, Page 296.  RTR Page 482.  [Tutorial](http://prideout.net/archive/bloom/index.php))
* Glare (Programming Vertex Geometry and Pixel Shaders, [Page 399](http://prelight.googlecode.com/files/Programming%20Vertex%20Geometry%20and%20Pixel%20Shaders.pdf))
* Watercolor (GPU Pro, Page 557) - edge detect following by smoothing
* 8-Bit (GPU Pro, Page 557)
* Kuwahara filter (GPU Pro, Page 247)
* Gamma Correction (RTR, Page 141)

Depth Buffer
* Depth of Field (Programming Vertex Geometry and Pixel Shaders, [Page 406](http://prelight.googlecode.com/files/Programming%20Vertex%20Geometry%20and%20Pixel%20Shaders.pdf).  GPU Gems, [Chapter 23](http://http.developer.nvidia.com/GPUGems/gpugems_ch23.html).  RTR, Page 486.  GPU Pro, Page 315.  )
* SSAO (RTR, Page 382.  Programming Vertex Geometry and Pixel Shaders, [Page 79](http://prelight.googlecode.com/files/Programming%20Vertex%20Geometry%20and%20Pixel%20Shaders.pdf).  GPU Pro, Page 215.  GPU Pro 2, Page 123)
* Fog (RTR, Page 496)

Later
* Motion blur using a velocity buffer (RTR, Page 490.  Programming Vertex Geometry and Pixel Shaders, [Page 410](http://prelight.googlecode.com/files/Programming%20Vertex%20Geometry%20and%20Pixel%20Shaders.pdf)).
* Glow with a glow buffer (GPU Gems, [Chapter 21](http://http.developer.nvidia.com/GPUGems/gpugems_ch21.html)).

Resources
* [Stylized Rendering in Spore](http://gpupro.blogspot.com/2010/05/stylized-rendering-in-spore.html)
* [Post Process Framework Sample](http://graphicsrunner.blogspot.com/2008/06/post-process-framework-sample.html)

-------

Water
* GPU Pro 2, Page 307
* ShaderX 2, [Page 207](http://tog.acm.org/resources/shaderx/Tips_and_Tricks_with_DirectX_9.pdf)
* A few demos from [Humus](http://www.humus.name/index.php?page=3D)
* [LEAN Mapping](http://www.csee.umbc.edu/~olano/papers/lean/)