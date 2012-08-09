While CZML can accurately describes a scene over time, CZML visualization is Cesium is limited to only showing data for the current time.  We can be expand the set of Cesium Visualizers to include both historical and future data; which primarily falls into two categories; paths and waypoints.

## Path Visualization
We use the more general term path, to describe the location of an object over time.  The idea behind path visualization is simple; for the DynamicObject.position property, create a Polyline showing where the object has been and where it is going.  We will expand the CZML specification to describe the graphics for this line as well as the amount of future (lead) and history (trail) time to show.  In addition to lead and trail times, it is sometimes convenient to show the entire path of an object, for example, driving directions from your house to the beach.  It's also desirable to show a fixed segment of the path that the object is on; for example a satellite's path circles the earth many times over, but we might only want to show the current "pass" it is on at the given time.

### CZML
Extending CZML to describe paths is simple.  All of the actual data we need is already included in the position property.  We just need to add a new "path" schema which describes the visualization of that data.  The superset of properties that describe the path are:

1. **color** - the color of the line
2. **width** - the width of the line
3. **outlineColor** - the color of the outline of the line
4. **outlineWidth** - the width of the outline
5. **show** - the visibility of the line
6. **leadTime** - the number of seconds of future data to show.  If omitted, all future data is shown.
7. **trailTime** - the number of seconds of historical data to show.  If omitted, all past data is shown.
8. **segments** - an array of ISO8601 intervals which denotes a segment of data to show whenever the current animation time is in or on the interval.

For flexibility, it would be nice if the lead portion, trail portion, and each interval segment could have it's own set of graphics properties.  So the actual schema can be laid our more hierarchically.

```
"path" : {
  lead : {
  },
  trail : {
  },
  segments : [
    {
    },
    {
    }
  ]
}
```

### DynamicScene

## Waypoint Visualization
For other visualizer types, such as billboard, show the past (and future) billboards which represent where we had actual (non-interpolated) data for.
