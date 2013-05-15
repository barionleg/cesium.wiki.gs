* Viewing in LLVH - [#531](https://github.com/AnalyticalGraphicsInc/cesium/issues/531)
* Draw plans perpendicular to orbits
* Stored views per track
* Render moon and other planets
* Sun centered views (Should ultimately support any CB as the center)
* Sensor improvements
   * Eliminate jitter - [#359](https://github.com/AnalyticalGraphicsInc/cesium/issues/359)
   * Narrow six-arc-second field-of-view.  Display condition to draw a polyline?
   * Narrow sensor like a fan
   * Wide sensor with a cap
   * Billboard aligned with sensor boresight (use a model?)
   * Draw a cone from the Sun to Earth's silhouette.  Compute custom sensor?

## Done

* ~~Render sun~~.
* ~~More precise sun position.~~ [#391](https://github.com/AnalyticalGraphicsInc/cesium/issues/391)
* ~~Inertial frame~~
* ~~Polyline - per-vertex color for passes.  Will [materials] (https://github.com/AnalyticalGraphicsInc/cesium/wiki/Fabric) on polylines work?~~
* ~~Ellipsoid improvements~~
   * ~~Eliminate jitter - [#392](https://github.com/AnalyticalGraphicsInc/cesium/issues/392)~~
   * ~~Zoom inside - [#390](https://github.com/AnalyticalGraphicsInc/cesium/issues/390)~~
   * ~~Covariance interpolation (in [czml-writer](https://github.com/AnalyticalGraphicsInc/czml-writer))~~