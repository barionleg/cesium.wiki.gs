Fabric is a JSON schema for describing materials in Cesium.  Materials represent the appearance of an object such as polygons and sensors.

Materials can be as simple as draping an image over an object, or applying a pattern such as stripes or a checkerboard.  Materials can be more complex such as procedural wood or view-dependent reflection and refraction.  Materials can be combined in a hierarchy to create new materials; for example, wet crumbling bricks can be created with a combination of procedural brick, bump map, and specular map materials.

<img src="features/CheckerboardMaterial.png" width="200" height="92" alt="Checkerboard" />
<img src="features/VerticalStripeMaterial.png" width="200" height="92" alt="Vertical stripe" />
<img src="features/DotMaterial.png" width="200" height="92" alt="Dot" /><br />
<img src="features/BrickMaterial.png" width="200" height="92" alt="Brick" />
<img src="features/WoodMaterial.png" width="200" height="92" alt="Wood" />
<img src="features/FacetMaterial.png" width="200" height="92" alt="Facet" />

Materials are applied to objects by assigning to the object's `material` property:
````
polygon.material = new Cesium.Material({
  context : scene.getContext(),
  fabric : {
    'id' : 'ColorMaterial'
  }
});
````

Cesium has several built-in materials that can be created without a full Fabric JSON:

* Procedural textures - checkerboard, stripes, dots, brick, cement, asphalt, wood, grass, distance intervals, tie-dye, facet, blob

* Color
* Image - a combination of diffuse and alpha map (described below) for representing images with an alpha channel such as .png.

* Diffuse map
* Specular map
* Alpha map
* Normal map
* Bump map
* Emission map
* Reflection
* Refraction
* Fresnel - a view-dependent combination of reflection and refraction.  Similar to water, when the viewer is looking straight down, the material is refracts light; as the viewer looks more edge on, the material refracts less and reflects more.

_TODO: screen shots and links to Sandcastle_
