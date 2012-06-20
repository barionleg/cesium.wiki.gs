**NOTE: This page is still a work in progress**

_This page describes implementation of the CZML standard in Cesium.  While not strictly required, it may help to check out the [CZML Language Guide](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Cesium-Language-%28CZML%29-Guide) and [Cesium Architecture overview](https://github.com/AnalyticalGraphicsInc/cesium/wiki/Architecture) before proceeding._

CZML support in Cesium can be broken down into 2 distinct pieces; processing and visualization.

The processing stage takes a CZML JSON object and creates and updates DynamicObject instances (and their associated DynamicProperty instances) within a DynamicObjectCollection.  Given a time, each individual DynamicProperty can return it's value at that time, interpolating between data points as necessary.  There are more advanced scenarios that involving streaming updates and CompositeDynamicObjectCollection, but we'll save those details of that for later.  The best part is that none of the CZML processing code depends on the Renderer or Scene layers of Cesium, which means it can be used, as is, to implement CZML support in any Javascript based application, including other virtual globes and maps.  As an aside, the fact that we use [asynchronous module definitions](http://requirejs.org/) also means that you won't be including code that you don't need.

Visualization is built on top of the DynamicObjectCollection which is populated during the processing stage.  This is done through a class of objects we simply call Visualizers, which usually map one aspect of a DynamicObject into Cesium graphic primitives; providing completely data-driven visualization.  This allows the developer to visualize any CZML document and only worry about his own application-specific code and requirements.  Once you understand the processing stage, visualization is incredibly straight-forward.

## Walkthrough of the Cesium CZML stack

So far, we've been speaking in very abstract terms, before we go into all of the low-level details, it might be better to walk through a more concrete example step by step.  This way you understaind how to use CZML in Cesium before understanding what is going on under the hood.

Starting out, we have the simple, yet complete CZML document show below.  It describes a single object, "Headquarters", which consist of three properties: id, position, and billboard.

```javascript
[
  {
    "id":"Headquarters",
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
      "image":"http://www.someImage.com/someImage.png",
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
//Download and parse a CZML file
var czml = JSON.parse(getJson('http://simpleBillboard.czml'));
//Create a DynamicObjectCollection for handling the CZML
var dynamicObjectCollection = new DynamicObjectCollection();
//Create the standard CZML visualizer collection
var visualizers = VisualizerCollection.createCzmlStandardCollection(scene, dynamicObjectCollection);
//Process the CMZL, which populates the collection with DynamicObjects
dynamicObjectCollection.processCzml(czml);
//Create a Clock object to drive time.
var clock = new Clock(startTime, stopTime);
```

Let's break this code up line by line and explain what's going on in each step.

First, we simply create the scene and parse the CZML document.  For simplicity, and the sake of this example, assume getJson is a magic function that synchronously retrieves the desired file from the server.

```javascript
var scene = new Scene(document.getElementById("canvas"));
var czml = JSON.parse(getJson('../simpleBillboard.czml'));
```
There's nothing fancy about this code; the end result is that czml is now a JSON object which contains CZML data.

Now that we have our CZML, we need to do something with it.  That's where DynamicObjectCollection comes in.

```javascript
var dynamicObjectCollection = new DynamicObjectCollection();
```
DynamicObjectCollection actually takes an optional parameter, updaterFunctions, which is an array of functions that perform the actual CZML processing.  Default constructing the object results in it using the standard set of updater functions that handle the full range of the CZML standard.  These default functions are specified in the CzmlStandard utility class.  In custom applications, you may only want to support a subset of the specification, or perhaps you want to extend the specification with custom properties.  In that case you would provide your own set of updater functions.  For this example, we use the defaults.

```javascript
var visualizers = VisualizerCollection.createCzmlStandardCollection(scene, dynamicObjectCollection);
```
Next we create our VisualizerCollection, which takes the DynamicObjects created by CZML and maintains equivalent graphic primitives for visualization.  Much like DynamicObjectCollection, VisualizerCollection offloads it's processing to individual visualizers which usually only create one type of primitive, for example there is a DynamicBillboardVisualizer which only handles billboards.  While you can construct the VisualizerCollection directly and provide your own set of visualizers, we use the helper function to create the full set that maps to the CZML standard.  Even though we've configured our objects, we haven't actually processed the CZML data yet, which happens on the next line.

```javascript
dynamicObjectCollection.processCzml(czml);
```

The processCzml call simply iterates over all of the CZML packets in our JSON object and take the following steps:

1. Check the id of the packet.  If the id does not exist, generate a GUID to represent this data point and create a new DynamicObject to represent it.  If the id property exists, it checks it's collection to see if an object of the same id exists, if not, it creates a new object with that id.

2. Once it has the correct DynamicObject, it calls each update function, passing in the individual CZML packet and the DynamicObject it applies.  This function will see if the packet has any relevant data, and if so merge that data into the existing DynamicObject.  In our example, two separate processor functions actually do something, DynamicObject.processCzmlPacketPosition and DynamicBillboard.processCzmlPacket, both of which are fairly self explanatory and create a position property and billboard property respectively.  It's important to note that while position is a single DynamicProperty, billboard is an aggregate object that contains several DynamicProperty instances, each relating to one aspect of the billboard.

TODO

## Processing

TODO

## Visualizers

TODO

**NOTE: This page is still a work in progress**