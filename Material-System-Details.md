Design and implementation ideas for our material system.

## Initial Features

* Add simple tests that verify the material by rendering a polygon.  Currently, we don't have tests for most materials.
* Explore materials implemented using procedural textures, i.e., brick, marble, granite, wood, asphalt, etc.  Later, we'll procedurally shade a city with these building blocks.
* Decouple diffuse and specular components.
   * Split `agi_getMaterialColor` into two separate GLSL functions: `agi_getMaterialDiffuseComponent` and `agi_getMaterialSpecularComponent`.
   * Add gloss/specular map material.
   * This will slightly impact the lighting code.
* Allow the material to modify the surface normal.
   * Add a third GLSL function that materials can optionally implement called `agi_getMaterialNormal` that takes and returns a normal.
   * Implement a bump map material using this.
* Add the world-space eye direction, i.e. the vector from the camera to the fragment in world coordinates, to `agi_getMaterial*` (or do we only need it for `agi_getMaterialDiffuseComponent` initially?).  Use this to implement:
   * A diffuse reflective material that uses an environment map for reflection, and a 2D texture for the diffuse component.  Blend these with a `reflectivity` parameter.
   * A diffuse refractive material that also uses an environment map.  Expose the two indices of refraction.
   * A Fresnel material - approximate, of course.
   * Include optional reflection and refractive maps for the above reflective and refractive materials, maybe Fresnel.

<!--
TBA: working with other lighting models?
TBA: deferred shading?
-->

## Full Features

* How does this fit with the effects framework for models?  They should work well together.
* How do we combine multiple materials, e.g.,
   * Blend two diffuse maps based on a parameter or third map.
   * A bump and specular map.
   * A bumpy diffuse reflective surface that combines the bump map and diffuse reflection materials.
   * Crumbling bricks that combine brick and bump map materials.
* Add materials to polylines.  Polylines will need to be able to compute at least 1D texture coordinates.  I could see some potential for 2D and 3D coordinates as well.

## Other Material Systems

* Effects frameworks like [CgFX](http://developer.nvidia.com/node/80) and COLLADA FX have materials as does every graphics engine under the sun, such as:
   * [Three.js](https://github.com/mrdoob/three.js/)
   * [Unity](http://unity3d.com/support/documentation/Manual/Materials)
   * [C4 Engine](http://www.terathon.com/wiki/index.php/Shaders)