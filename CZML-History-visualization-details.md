While CZML can accurately describes a scene over time, CZML visualization in Cesium is limited to only showing data for the current time.  We can be expand the set of Cesium Visualizers to include both historical and future data, which primarily falls into two categories: paths and waypoints.

## Status
At current head of master we have basic path visualization support as outlined below.  In places where we propose a number of options, we've marked which option we are currently using in the code.

## Path Visualization
We use the more general term path, to describe the location of an object over time.  The idea behind path visualization is simple; for the DynamicObject.position property, create a Polyline showing where the object has been and where it is going.  We will expand the CZML specification to describe the graphics for this line as well as the amount of future (lead) and history (trail) time to show.  In addition to lead and trail times, it is sometimes convenient to show the entire path of an object, for example, driving directions from your house to the beach.

### CZML
Extending CZML to describe paths is simple.  All of the actual data we need is already included in the position property.  We just need to add a new "path" schema which describes the visualization of that data.  The superset of properties that describe the path are:

1. **color** - the color of the line
2. **width** - the width of the line
3. **outlineColor** - the color of the outline of the line
4. **outlineWidth** - the width of the outline
5. **show** - the visibility of the line
6. **leadTime** - the number of seconds of future data to show.  If omitted, all future data is shown.
7. **trailTime** - the number of seconds of historical data to show.  If omitted, all past data is shown.

And a simple CZML example
```
"path" : {
  "color" : { "rgba" : [255, 255, 255, 255] },
  "outlineColor" : { "rgba" : [0, 0, 0, 255] },
  "width" : 3,
  "outlineWidth" : 2
  "lead" : 60,
  "trail" : 60,
}
```
Finally, it's important to recognize that the path graphics are actually identical to the Polyline graphics that already exist in CZML, so each of these objects will actually inherit from Polyline in the schema.  In the future, we will be enhancing Polyline to include additional options, such as per-point colors.  When that happens, those enhancements will also carry-over to Path.

### DynamicScene
Now that we've defined the Path object in CZML, we need to add support for it in the Cesium DynamicScene layer.  Much like other visualizers, this can be encapsulated into two objects.

* **DynamicPath** - a data-only object which will handle processing the CZML path properties into DynamicProperty instances.  This will map to a DynamicObject.path property.
* **DynamicPathVisualizer** - a Visualizer which will turn the DynamicObject.path instances on each object into Polyline primitives.

Additionally, since the DynamicPolylineVisualizer and DynamicPathVisualizer will both be working with Polyline instances, it would be beneficial to extract out common updating code into a **PolylineUpdater** helper object in DynamicScene, which each visualizer can use to maintain all non-vertex aspects of the polyline.

So far everything has been relatively straightforward, we're just turning CZML into properties and then mapping those properties into primitives via the visualizers.  The trickiest part of this entire process lies in sampling the DynamicObject.position property so that we can accurately represent the line.  This process has several pit-falls.

1. If we under-sample the line, smooth curves will start to appear jagged and paths that go around the earth or terrain may end up actually going through them.  For example, if we sample a satellite at 60 second steps, it will probably look pretty good and perform well; however if I'm rendering my morning drive to work, a 60 second step will miss segments of the route completely, such as my turn off the exit and through the toll booth.
2. If we end up over-sampling the line, performance may suffer to the point of being unusable.  For example, if we lower our step size to 5 seconds in order to make my previously mentioned drive look good, the satellite we were rendering will now create way too many unnecessary data points for the polyline.
3. There are certain points along the path that you always want to step onto exactly, for example if we have a billboard drawn for my current location I need to make sure I always sample that location, or else the billboard will not actually be on my path.  Not only will this look weird, its also just wrong.  Additionally, we might want to step on the actual waypoints provided by the CZML, this way we don't miss significant positions that might be easily missed by sampling.

Unless the path is simply a straight line, all three of these problems will occur at one time or another and makes implementation tricky.  There are two primary sampling methods we can use to generate a polyline.

1. **Fixed step** - While this is not the ideal final solution, it can go a long way for a majority of uses cases.  It's also easiest to implement.  The most naive way to do so is determine the total amount of time you need to sample; divide by a constant value (say 100) to get your step size; and then sample the line in a for loop.  Congratulations, we've just crashed head first into all 3 of the pitfalls listed above.  Thankfully, these can be partially mitigated.  We start by getting a list of all of the actual waypoints stored in the DynamicPositionProperty.  We then perform fixed step sampling between each waypoint.  We also sample at the current animation time, this way any primitives that are only showing the current time, like in our billboard example above, will actually be on the line.  This eliminates pitfall number 3, but it only lessens 1 and 2.  It's still possible to under and over sample because we're taking fixed steps regardless of the length of the line.  So a 2 pixel long line and a 1500 pixel long line get the same number of data vertices.
2. **Tessellation** - We start off by defining a "pixel error tolerance" which is the number of pixels which a rendered path can deviate from where it would appear if it were perfectly sampled.  A value of 0 indicates "pixel perfect" sampling.  Using the list of defined waypoints and the object's current position, similar to the above.  We then create pairs of line segments from the waypoints.  In a loop, we continuously sub-divide these into smaller segments by sampling at the center time of each segment.  This creates shorter and shorter segments with waypoints that are closer together.  When the pixel distance between two waypoints is less than or equal to the pixel tolerance, we stop sampling.  This eliminates all 3 of the concerns we initially noted (except for possible oversampling of straight lines) but suffers from one major drawback; performance.  Because this solution is view based, the path needs to be recalculated every time the camera moves.  I'm unsure if we can offload any of this processing to the video card.  We might be able to help performance by using web-workers to perform the tessellation.  We can also limit the amount of times we re-calculate our lines by only doing so when the camera position and orientation changes by some tolerance.  Finally, it should be possible to re-use the results of the last computation as input when recomputing, making the entire process go much faster.  Obviously, much more experimentation is required to determine the optimal methods.
3. **Use source data** - Simply use the waypoints actually defined in the data and do not sample the line at all.  This will be fastest, but suffers from pitfall one.  Pitfall 2 can't happen and 3 is easily mitigated

At current head of `master`, we have implemented option 3, but will continue to explore other options as time/priority allows.

### Reference Frames
A problem that we have not yet touched on is reference frames.  For example, Satellite orbits are better drawn in the inertial frame while aircraft routes used fixed.  Since reference frames are not implemented on the client side yet, everything is currently drawn in the fixed frame.  The ultimately plan is to add support for reference frames and then draw the data in the same frame that it is defined in the CZML.

Feed-back is always appreciated one our [development mailing list](https://groups.google.com/d/forum/cesium-dev). 

## Waypoint Visualization (TBD)
For other visualizer types, such as billboard, show the past (and future) billboards which represent where we had actual (non-interpolated) data for.