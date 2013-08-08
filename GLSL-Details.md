Design and implementation ideas for our GLSL shader system.

## Features

* Auto `#include` functions, types, etc. starting with `agi_`. Most of these are in .glsl files, but some are prepended at runtime, but don’t have to be. Search for `getBuiltinConstants` in `ShaderProgram.js`.
* In addition to auto includes, I suppose we need manual includes for things like `SensorVolume.glsl`, which are not global across Cesium, but useful for a few primitives.
* Report useful line numbers from compile/link warning/errors.
* Work well with uber-shaders determined at runtime. Search for `getShaderProgram` in `CentralBody.js`.
* Work well with our material system, which dynamically creates shaders – think GLSL compile-time polymorphism. Each shader implementations a virtual function so-to-speak, e.g., see `VerticalStripeMaterial` and its shader, `VerticalStripeMaterial.glsl`. Anyone who can use a material calls this "virtual function." For a simple example, search for `getShaderProgram` in `Polygon.js`. A single primitive may have multiple materials for different surfaces (rendered in the same pass), so I rename uniforms like I am an out-of-order processor renaming registers. Search for `combine` in `ComplexConicSensorVolume.js`.
* Control over precision used in the fragment shader. This is particularly important for mobile performance. See `getShaderPrecisionFormat`.
* Handle precision correctly - [#817](https://github.com/AnalyticalGraphicsInc/cesium/issues/817)
* GLSL optimization and minification like glTF issues [#36](https://github.com/KhronosGroup/glTF/issues/36) and [#34](https://github.com/KhronosGroup/glTF/issues/34).
* Performance idea:  async shader compile/link.  Let's time `linkProgram` first because I think that is actually synchronous on most drivers.

## Resources

* [GLSL Minifier Open Sourced](https://groups.google.com/forum/?fromgroups#!topic/webgl-dev-list/RkGgA0t9IUA)
* [gloc](http://ashimaarts.com/gloc/)
* [glfx](http://code.google.com/p/glfx/)