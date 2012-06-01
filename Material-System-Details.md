Design and implementation ideas for our material system.

## Phase 1

* _Done: Add simple tests that verify the material by rendering a polygon.  Currently, we don't have tests for most materials._
* _Done: Explore materials implemented using procedural textures, i.e., brick, marble, granite, wood, asphalt, etc.  Later, we'll procedurally shade a city with these building blocks._
* _Done: Add better reference documentation._
* Add an opacity/alpha map material.
* Decouple diffuse and specular components.
   * Split `agi_getMaterialColor` into two separate GLSL functions: `agi_getMaterialDiffuseComponent` and `agi_getMaterialSpecularComponent`.
   * Add gloss/specular map material.
   * This will slightly impact the lighting code.
* Allow the material to modify the surface normal.
   * Add a third GLSL function that materials can optionally implement called `agi_getMaterialNormal` that takes and returns a normal.
   * Implement a bump map material using this.  Implement a normal map material too.
* Add the world-space eye direction, i.e. the vector from the camera to the fragment in world coordinates, to `agi_getMaterial*` (or do we only need it for `agi_getMaterialDiffuseComponent` initially?).  Use this to implement:
   * A diffuse reflective material that uses an environment map for reflection, and a 2D texture for the diffuse component.  Blend these with a `reflectivity` parameter.
   * A diffuse refractive material that also uses an environment map.  Expose the two indices of refraction.
   * A Fresnel material - approximate, of course.
   * Include optional reflection and refractive maps for the above reflective and refractive materials, maybe Fresnel.

## Phase 2

* Polylines
   * Polylines currently use very simple shaders, and are rendered in three passes using the stencil buffer to achieve an outline effect (turn ANGLE off; start Chrome with `--use-gl=desktop`).
   * Replace the three-pass algorithm with a single pass algorithm that, in a fragment shader, uses the distance from the fragment to the line to determine if the fragment is part of the outline.  Read [Tron, Volumetric Lines, and Meshless Tubes](http://prideout.net/blog/?p=61).
   * First hard-code the above in the Polyline, then factor it out into a new `PolylineOutlineMaterial`.
   * Create a `PolylineGlowMaterial` based on [Tron, Volumetric Lines, and Meshless Tubes](http://prideout.net/blog/?p=61).
   * Make Polylines work with the rest of the materials as reasonable.  Polylines will need to be able to compute at least 1D texture coordinates.  I could see some potential for 2D and 3D coordinates as well.  All materials will not work with all primitives.  We'll need to document a feature matrix.

## Phase 3

<!--
TBA: working with other lighting models?
TBA: deferred shading?
-->

* How do we combine multiple materials, e.g.,
   * A diffuse map and a specular map.
   * Crumbling bricks that combine brick and bump map materials.
   * A bumpy diffuse reflective surface that combines the bump map and diffuse reflection materials.
   * A diffuse map, diffuse reflective, specular map, and bump map.  A bumpy, diffuse lit and reflective surface with shiny areas.
   * Blend two diffuse maps based on a parameter or third map.

## Phase 4

* How does this fit with the effects framework for models?  Can they work well together?

## Other Material Systems

* Effects frameworks like [CgFX](http://developer.nvidia.com/node/80) and COLLADA FX have materials as does every graphics engine under the sun, such as:
   * [Three.js](https://github.com/mrdoob/three.js/)
   * [Unity](http://unity3d.com/support/documentation/Manual/Materials)
   * [C4 Engine](http://www.terathon.com/wiki/index.php/Shaders)
   * [Id tech 4](http://www.modwiki.net/wiki/Texturing)