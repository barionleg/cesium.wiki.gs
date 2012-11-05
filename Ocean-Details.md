Implementation ideas for rendering the ocean.

* Implement by creating a material with [Fabric](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Fabric).
* Use a specular map so we know what is water and what is land.  Let's not worry about the resolution for the moment.  Coastlines will look bad.  Also use the specular map so when water is near land,
   * it flows differently
   * it is shallower and therefore animates and renders differently.
* We have noise functions to animate the water.  Check the reference help for our GLSL built-ins.
* Fresnel - reflection and refraction depend on the view angle.
* A nice WebGL [demo](http://29a.ch/sandbox/2012/terrain/) and [details](http://29a.ch/2012/7/19/webgl-terrain-rendering-water-fog).

## Resources

* Must read: [Regarding Water](http://the-witness.net/news/2012/08/regarding-water/)
* GPU Pro 2, Page 307
* ShaderX 2, [Page 207](http://tog.acm.org/resources/shaderx/Tips_and_Tricks_with_DirectX_9.pdf)
* A few words in [LEAN Mapping](http://www.csee.umbc.edu/~olano/papers/lean/)
* A few demos from [Humus](http://www.humus.name/index.php?page=3D)
