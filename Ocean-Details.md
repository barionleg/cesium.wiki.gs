Implementation ideas for rendering the ocean.

* Fresnel - reflection and refraction depend on the view angle.
* Use specular map so when water is near land,
   * it flows differently
   * it is shallower and therefore animates and renders differently.
* Use dynamic branch to discard fragments based on distance. No need to perform all the wave sampling when the `fadeFactor` is going cancel out the effect.
* Utilize the alpha channel in the `baseWaterColor` and `blendColor` to add additional translucency to the water. May be useful to view terrain, models, etc. under the water.

## Done

* _Done:_ Implement by creating a material with [Fabric](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Fabric).
* _Done:_ We have noise functions to animate the water.  Check the reference help for our GLSL built-ins.
* _Done:_ Use a specular map so we know what is water and what is land.  Let's not worry about the resolution for the moment.  Coastlines will look bad.

## Resources

* [Assassin’s Creed III: The tech behind (or beneath) the action](http://www.fxguide.com/featured/assassins-creed-iii-the-tech-behind-or-beneath-the-action/)
* Must read: [Regarding Water](http://the-witness.net/news/2012/08/regarding-water/)
* GPU Pro 2, Page 307
* ShaderX 2, [Page 207](http://tog.acm.org/resources/shaderx/Tips_and_Tricks_with_DirectX_9.pdf)
* A few words in [LEAN Mapping](http://www.csee.umbc.edu/~olano/papers/lean/)
* A few demos from [Humus](http://www.humus.name/index.php?page=3D)
* WebGL Demos
   * WebGL Terrain, Ocean, Fog: [demo](http://29a.ch/sandbox/2012/terrain/), [blog post](http://29a.ch/2012/7/19/webgl-terrain-rendering-water-fog)
   * WebGL GPU Landscaping and Erosion: [demo](http://codeflow.org/webgl/craftscape/), [blog post](http://codeflow.org/entries/2011/nov/10/webgl-gpu-landscaping-and-erosion/)