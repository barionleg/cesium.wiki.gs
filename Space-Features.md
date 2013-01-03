* Inertial frame
* Viewing in LLVH
* Ellipsoid improvements
   * Eliminate jitter - [#392](https://github.com/AnalyticalGraphicsInc/cesium/issues/392)
   * Zoom inside - [#390](https://github.com/AnalyticalGraphicsInc/cesium/issues/390)
* Polyline - per-vertex color for passes.  Will [materials](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Fabric) on polylines work?
* More precise sun position - [#391](https://github.com/AnalyticalGraphicsInc/cesium/issues/391)
* Covariance interpolation (in [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer))
* Stored views per track
* Sensor improvements
   * Eliminate jitter - [#359](https://github.com/AnalyticalGraphicsInc/cesium/issues/359)
   * Narrow six-arc-second field-of-view.  Display condition to draw a polyline?
   * Narrow sensor like a fan
   * Wide sensor with a cap
   * Billboard aligned with sensor boresight (use a model?)
   * Draw a cone from the Sun to Earth's silhouette.  Compute custom sensor?