* Polyline - per-vertex color for passes.  Will [materials](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Fabric) on polylines work?
* More precise sun position - #391
* Covariance interpolation (in [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer))
* Stored views per track

* Ellipsoid improvements
   * Eliminate jitter - #392
   * Zoom inside - #390

* Sensor improvements
   * Eliminate jitter - #359
   * Narrow six-arc-second field-of-view.  Display condition to draw a polyline?
   * Narrow sensor like a fan
   * Wide sensor with a cap
   * Billboard aligned with sensor boresight (use a model?)
   * Draw a cone from sun to Earth's silhouette.  Compute custom sensor?