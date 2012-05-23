# Roadmap

## Always

We're always looking to:
* Write demos that showcase Cesium, especially demos that combine Cesium with other web APIs.
* Support more content by writing converters from other formats to CZML using our [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer) library.
* Write tutorials and improve reference documentation and examples.
* Improve visual quality and performance.
* Improve platform support by fixing issues on various browsers, devices, or video cards.
* Improve tests and test coverage; however, we don't blindly chase coverage statistics.

## Near term
* [[CZML|Cesium Language (CZML) Guide]] Visualization
* Imagery layers - [details](Imagery-Layers-Details)
* Flesh out material system - [details](Material-System-Details)
* COLLADA models
* Streaming terrain
* Stars
* Data-driven renderer
   * Improved depth-buffer precision
   * Culling for all objects
   * Post-processing framework
* Improve 3D/2D/Columbus view transitions
* Improve mobile support
* Improve precision - remove potential jittering

## Longer term
* Support for multiple central bodies, i.e., Sun, Moon, etc.
* Build and test server
* Shadows
* Video on terrain
* Vectors
* Render buildings
* Label declutter
* Polyline and polygon LOD.  [Douglas-Peucker reduction](http://www.bowdoin.edu/~ltoma/teaching/cs350/spring06/Lecture-Handouts/hershberger92speeding.pdf)
* John Madden-style collaboration among multiple clients
* Particle system
* Ocean
* Volumetric clouds