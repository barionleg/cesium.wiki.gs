**NOTE: This page is still a work in progress**

_This page describes implementation of the CZML standard in Cesium.  While not strictly required, it may help to check out the [[CZML-Guide]] and [Cesium Architecture](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture) overview before proceeding._

CZML support in Cesium can be broken down into two distinct pieces; processing and visualization.

The processing stage takes a CZML JSON object, and creates and updates `DynamicObject` instances (and their associated `DynamicProperty` instances) within a `DynamicObjectCollection`.  Given a time, each individual `DynamicProperty` can return its value at that time, interpolating between data points as necessary.  There are more advanced scenarios that involve streaming updates and `CompositeDynamicObjectCollection`, but we'll save those for later.  The best part is that none of the CZML processing code depends on the Renderer or Scene layers of Cesium, which means it can be used, as is, to implement CZML support in any Javascript based application, including other virtual globes and maps.  As an aside, since we use [asynchronous module definitions](http://requirejs.org/), Cesium apps don't have to include code they don't need.

Visualization is built on top of the `DynamicObjectCollection` which is populated during the processing stage.  This is done through a class of objects called `Visualizers`, which usually map one aspect of a `DynamicObject` into Cesium graphic primitives; providing completely data-driven visualization.  This allows us to visualize any CZML document and only worry about our own application-specific code and requirements.  Once we understand the processing stage, visualization is incredibly straightforward.

## Walkthrough of the Cesium CZML stack

So far, we've spoke in abstract terms.  Before we go into the low-level details, let's walk through a concrete example step by step so we understaind how to use CZML in Cesium before understanding what is going on under the hood.

Starting out, we have the simple, yet complete CZML document show below.  It describes a single object, "Headquarters", which consist of three properties: id, position, and billboard.

```javascript
[
  {
    "id":"Headquarters",
    "availability":"2012-06-20T16:00:00Z/2012-06-20T16:02:00Z",
    "position":{
      "cartesian":[
        1216469.9357990976,-4736121.71856379,4081386.8856866374
      ]
    },
    "billboard":{
      "color":{
        "rgba":[
          0,255,255,255
        ]
      },
      "horizontalOrigin":"CENTER",
      "image":"http://cesiumjs.org/images/Cesium_Logo.png",
      "scale":1.0,
      "show":[
        {
          "interval":"2012-06-20T16:00:00Z/2012-06-20T16:02:00Z",
          "boolean":true
        }
      ],
      "verticalOrigin":"CENTER"
    }
  }
]
```

Assuming we wanted to visualize this data in a simple Cesium application, such as the Skeleton available in the Examples directory, the code would like something like the below.

```javascript
//Create a scene
var scene = new Scene(document.getElementById("canvas"));
//Create a DynamicObjectCollection to contain the objects from CZML
var dynamicObjectCollection = new DynamicObjectCollection();
//Create the standard CZML visualizer collection
var visualizers = VisualizerCollection.createCzmlStandardCollection(scene, dynamicObjectCollection);
//Create a Clock object to drive time.
var clock = new Clock();
//Download and parse a CZML file asynchronously
var czmlUrl = 'http://cesiumjs.org/someFile.czml';
getJson(czmlUrl).then(function(czml) {
    //Process the CZML, which populates the collection with DynamicObjects
    processCzml(czml, dynamicObjectCollection, czmlUrl);
    //Figure out the time span of the data
    var availability = dynamicObjectCollection.computeAvailability();
    clock.startTime = availability.start;
    clock.stopTime = availability.stop;
});
```

After the initial set-up, we call `update` in our `requestAnimationFrame` callback.

```javascript
var currentTime = clock.tick();
visualizers.update(currentTime);
```

Let's break this code up line by line and explain what's going on in each step.

First, we create the scene and parse the CZML document.

```javascript
var scene = new Scene(document.getElementById("canvas"));
//Download and parse a CZML file asynchronously
var czmlUrl = 'http://cesiumjs.org/someFile.czml';
getJson(czmlUrl).then(function(czml) {
});
```
This code asynchronously requests CZML from the given URL, then calls a function with the parsed JSON once it's been retrieved.

Now that we have our CZML, we need to do something with it.  That's where `DynamicObjectCollection` comes in.

```javascript
var dynamicObjectCollection = new DynamicObjectCollection();
```
DynamicObjectCollection takes an optional parameter, `updaterFunctions`, which is an array of functions that perform the actual CZML processing.  Default constructing the object results in it using the standard set of updater functions that handle the full range of the CZML standard.  These default functions are specified in the `CzmlDefaults` utility class.  In custom applications, we may only want to support a subset of the specification, or perhaps we'll want to extend the specification with custom properties.  In those cases, we would provide our own updater functions.  For this example, we use the defaults.

```javascript
var visualizers = VisualizerCollection.createCzmlStandardCollection(scene, dynamicObjectCollection);
```
Next we create our `VisualizerCollection`, which takes the `DynamicObject`s created by CZML, and maintains equivalent graphic primitives for visualization.  Much like `DynamicObjectCollection`, `VisualizerCollection` offloads its processing to individual visualizers which usually only create one type of primitive; for example, there is a `DynamicBillboardVisualizer` which only handles billboards.  While we can construct the `VisualizerCollection` directly, and provide our own set of visualizers, we use the helper function to create the full set that maps to the CZML standard.  Even though we've configured our objects, we haven't actually processed the CZML data yet, which happens on the next line.

```javascript
processCzml(czml, dynamicObjectCollection, czmlUrl);
```

The `processCzml` function iterates over all of the CZML packets in our JSON object taking the following steps:

1. Check the id of the packet.  If the id does not exist, generate a GUID to represent this data point and create a new `DynamicObject` to represent it.  If the id property exists, check its collection to see if an object of the same id exists, if not, it creates a new object with that id.

2. Once it has the correct `DynamicObject`, it calls each update function, passing in the individual CZML packet and the `DynamicObject` it applies.  This function will see if the packet has any relevant data, and if so merge that data into the existing `DynamicObject`.  In our example, two separate processor functions actually do something, `DynamicObject.processCzmlPacketPosition` and `DynamicBillboard.processCzmlPacket`, both of which are fairly self explanatory and create a position property and billboard property, respectively.  While position is a single `DynamicProperty`, billboard is an aggregate object that contains several `DynamicProperty` instances, each relating to one aspect of the billboard.

When the function returns, `dynamicObjectCollection` includes all of the dynamic objects present in the CZML.  `DynamicObjectCollection` will also fire events for interested parties when new object properties are available - more on that later.

```javascript
var clock = new Clock();

//Figure out the time span of the data
var availability = dynamicObjectCollection.computeAvailability();
clock.startTime = availability.start;
clock.stopTime = availability.stop;
```

Finally, we create a `Clock` object to manage time.  `Clock` takes a few other optional parameters, check the reference documentation for details.  In order to find out what time span our CZML file covers, we call `dynamicObjectCollection.computeAvailability` which returns a `TimeInterval` of available data, which we then set on the clock.

Now that we have loaded our CZML and configure our Visualizers, it's just a matter of telling the clock to advance and our visualizers to update each frame.

```javascript
var currentTime = clock.tick();
visualizers.update(currentTime);
```
`clock.tick` returns the new current time, but `clock.currentTime` will also have the new value.  The `VisualizerCollection` iterates over all of the underlying visualizer instances, and calls update on each one.  Each visualizer is then responsible for updating primitives for each of the dynamic objects in the dynamicObjectCollection.

Thus far, we discussed the basics of loading and visualizing CZML with Cesium.  In the next sections, we'll go further under the hood to discuss exactly what's going as well as explore advanced use cases such as streaming and compositing CZML documents.

## Processing

TODO

## Visualizers

TODO

**NOTE: This page is still a work in progress**