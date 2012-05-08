Cesium is a client-side library written in JavaScript.  The Cesium stack is coarsely organized and composed of four layers:

<img src="architectureFigures/clientStack.png" width="50%" />

Generally, each layer adds functionality, raises the level of abstraction, and depends on the layers underneath it.  The layers are:
* _Core_ - number crunching like linear algebra, intersection tests, and interpolation.
* _Renderer_ - a thin abstraction over [WebGL](http://www.khronos.org/webgl/).
* _Scene_ - globe and map constructs like imagery layers, polylines, labels, and cameras.
* _Dynamic Scene_ - Time-dynamic constructs including [CZML](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Cesium-Language-%28CZML%29-Guide) rendering.

Each layer corresponds to one directory in the [source tree](https://github.com/AnalyticalGraphicsInc/cesium/tree/master/Source).  All layers are available to applications built using Cesium.  All apps use Core.  As shown below, a small subset of apps use Renderer, many apps use Scene, and perhaps the most apps, such the Cesium Viewer, use Dynamic Scene.

<img src="architectureFigures/invertedPyramid.png" width="50%" />

## Core

```javascript
```

<img src="architectureFigures/core.png" width="30%" />

## Renderer

<img src="architectureFigures/renderer.png" width="30%" />

## Scene

<img src="architectureFigures/scene.png" width="30%" />

## Dynamic Scene

<img src="architectureFigures/dynamicScene.png" width="30%" />