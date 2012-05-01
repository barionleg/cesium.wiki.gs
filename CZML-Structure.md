_NOTE: This is a work in progress and reflects our plans NOT our current capabilities._

CZML is a subset of [JSON](http://www.json.org), meaning that a valid CZML document is also a valid JSON document.  Specifically, a CZML document contains a single JSON array where each object-literal element in the array is a CZML packet.  A CZML packet describes the graphical properties for a single object in the scene, such as a single aircraft.

_Note: we use javascript comments in these examples even though comments are not technically allowed in JSON._

```javascript
[
    // packet one
    {
        "id": "GroundControlStation"
        "position": { "cartographicDegrees": [-75.5, 40.0, 0.0] },
        "point": {
            "color": { "rgba": [0, 0, 255, 255] },
        }
    },
    // packet two
    {
        "id": "PredatorUAV",
        // ...
    }
]
```

Each packet has an `id` property identifying the object it is describing.  IDs do not need to be GUIDs - URIs make good IDs - but they do need to uniquely identify a single object within a CZML source and any other CZML sources loaded into the same scope. We'll talk more about scopes later in this document.

If an `id` is not specified, the client will automatically generate a unique one. However, this prevents later packets from referring to this object in order to, for example, add more data to it.

In addition to the `id`, packets contain zero or more (but usually one or more) properties defining the graphical characteristics of the object.  In the example above, we've specified that the "GroundControlStation" object has a fixed position at [WGS 84](http://en.wikipedia.org/wiki/World_Geodetic_System) longitude -75.5 degrees, latitude 40.0 degrees, and height 0.0 meters, and that a blue point (dot) is drawn at its location.

There are many standard properties defined for CZML, including properties for adding points, billboards, models, lines, and other graphics to the scene.  The available properties are described in detail on the [[CZML Content]] page.  On this page, we are primarily concerned with how the data is structured.  For example, we describe how a property can be specified such that it has two different values over two different intervals of time.

## Intervals

In the most general case, the value of a CZML property is a JSON array, where each element in the array is an object literal defining the value of the property for a different interval of time.  The interval described by any given object literal in the array is specified using an [ISO8601 interval](http://en.wikipedia.org/wiki/ISO_8601#Time_intervals) string in the `interval` property.

```javascript
{
    "id": "myObject",
    "someProperty": [
        {
            "interval": "2012-04-30T12:00:00Z/13:00:00Z",
            "number": 5
        },
        {
            "interval": "2012-04-30T13:00:00Z/14:00:00Z",
            "number": 6
        },
    ]
}
```

Here we define the `someProperty` property over two intervals, the first from noon to 1:00 PM UTC where the value of the property is 5, and the other from 1:00 PM to 2:00 PM UTC where the value of the property is 6.  The value will change instantly when crossing the boundary between two intervals.  We use `number` to indicate the value because this is a number-type property.  Some properties, notably properties that represent position, allow the value to be specified in multiple formats, such as a Cartesian X,Y,Z position or a Cartographic longitude, latitude, height position.  The [[CZML Content]] page lists the types of data supported for each property, and the value names to use with each.

The `interval` property is optional.  If it is not specified, the interval is assumed to span all time.  It doesn't make much sense to specify multiple infinite intervals, or intervals that overlap in general, but if you do, the one later in the CZML file or stream takes precedence.

In the common case that the property has a value over just one interval, the interval list array can be omitted entirely.

```javascript
{
    "id": "myObject",
    "someProperty": {
        "interval": "2012-04-30T12:00:00Z/14:00:00Z",
        "number": 5
    }
}
```

Just as before, the `interval` property can be omitted if it spans all time.  For properties with simple values, like the number property shown above, and with a single value for all time, the value can be given even more compactly:

```javascript
{
    "id": "myObject",
    "someProperty": 5
}
```

This abbreviated notation is valid for any property whose value can be represented with one of the simple JSON data types: string, number, or boolean.

## Composite Values

More complicated composite values, such as a Cartesian position or a color, are represented using JSON arrays.  For a Cartesian position, the array has three elements, corresponding to the X, Y, and Z components of the position, respectively.

```javascript
{
    "id": "myObject",
    "someComplexProperty": {
        "cartesian": [1.0, 2.0, 3.0]
    }
}
```

Composite values must always be specified within an interval, even if that interval is infinite as shown here.  If the value, `[1.0, 2.0, 3.0]`, were allowed as the value of the `complexProperty` directly, it would be necessary for a client interpreting the CZML to look at the contents of the array to determine whether the array is a list of intervals or a single value.  So, for simplicity, we do not allow this.

The [[CZML Content]] page describes how various types of data are encoded in arrays.

## Sampled Property Values

So far, we've discussed how to specify a single value for a property for all time, and how to specify different values for a property over different discrete intervals.  Some properties (and the [[CZML Content]] page will tell you which) also allow you to specify time-tagged samples which the client will interpolate over to compute the value of the property at any given time.  Times are specified using [ISO8601](http://en.wikipedia.org/wiki/ISO_8601) strings.

```javascript
{  
    // ...  
    "someInterpolatableProperty": {  
        "cartesian": [  
            "2012-04-30T12:00Z", 1.0, 2.0, 3.0,  
            "2012-04-30T12:01Z", 4.0, 5.0, 6.0,  
            "2012-04-30T12:02Z", 7.0, 8.0, 9.0  
        ]  
    }  
} 
```

Here we're specifying that the value is `[1.0, 2.0, 3.0]` at noon, `[4.0, 5.0, 6.0]` one minute later, and `[7.0, 8.0, 9.0]` a minute after that.  If the client's current clock is 30 seconds past noon, the value will be a linear interpolation between `[1.0, 2.0, 3.0]` and `[4.0, 5.0, 6.0]`, or `[2.5, 3.5, 4.5]`.

For succinctness, times can also be specified in seconds since an epoch.  While this is potentially less precise than specifying each time using an ISO8601 string, it is usually more than sufficient when the samples span less than a day or when the offsets are whole numbers of seconds.

```javascript
{  
    // ...  
    "someInterpolatableProperty": {  
        "epoch": "2012-04-30T12:00Z",  
        "cartesian": [  
            0.0, 1.0, 2.0, 3.0,  
            60.0, 4.0, 5.0, 6.0,  
            120.0, 7.0, 8.0, 9.0  
        ]  
    }  
}
```

Finally, properties specified using time-tagged samples have some additional, optional sub-properties controlling interpolation.

```javascript
{  
    // ...  
    "someInterpolatableProperty": {  
        "epoch": "2012-04-30T12:00Z",  
        "cartesian": [  
            0.0, 1.0, 2.0, 3.0,  
            60.0, 4.0, 5.0, 6.0,  
            120.0, 7.0, 8.0, 9.0  
        ],  
        "interpolationAlgorithm": "LAGRANGE",  
        "interpolationDegree": 5
    },  
} 
```

The `interpolationAlgorithm` specifies the algorithm to use to interpolate a value at a different time from the provided data.  The available algorithms are described on the [[CZML Content]] page.  The `interpolationDegree` property specifies the degree of the polynomial to use for interpolation.  For example, `1` means linear interpolation and `2` means quadratic interpolation.  If these properties are not specified, linear interpolation is used.

It is not necessary for the time of every sample to fall within the interval that contains it, but the samples will not be used outside their interval.  This is useful to provide better accuracy with higher-degree interpolation.

## EventSource and Streaming

Putting an entire CZML document in one big JSON array makes it difficult to load the document incrementally.  Today's web browsers allow some access to a stream before it is complete, but parsing and interpreting the incomplete data requires slow and cumbersome string manipulations.  To faciliate high-performance streaming, CZML may also be streamed using modern browsers' [server-sent events](http://dev.w3.org/html5/eventsource/) (`EventSource`) API.  When using this API, each CZML packet is streamed to the client as a separate event:

```javascript
event: czml
data: {  
    // packet one  
}  
  
event: czml
data: {  
    // packet two  
} 
```

As a result, the browser raises an event when each packet is received, containing the data for just that one packet.  This allows us to incrementally process CZML data with excellent performance.

So far, we've perhaps implied that a single object is represented using a single packet that describes all of the graphics associated with that object.  But this is not necessarily the case.  A single CZML stream or document can contain multiple packets with the same `id`, describing different aspects of the same object.

In fact, in some cases, two packets can even describe the same property of an object.  This is useful when the property is defined over many intervals or when an interval contains many time-tagged samples.  By breaking the complete definition of a property into multiple packets, we can get relevant data into Cesium sooner to minimize the time that the user must wait before Cesium starts rendering the scene.

When a client receives a CZML packet, it walks through each property contained in the packet.  For each property, it walks through each interval over which the property is defined.  For each interval, it determines if the specified interval has already been defined for the property.  If the interval has already been defined, the existing interval is updated; otherwise, a new one is created.

When updating an existing interval, any provided sub-property value replaces the existing value, if any.  The only exception is when both the previous property value and the new property value contain time-tagged samples.  In that case, the samples are added to the list of samples for that interval.

When a new interval overlaps existing intervals, the new interval takes precedence and the existing intervals are truncated or removed entirely.  This is important to keep in mind because later intervals will be tested against the truncated intervals when determining whether the interval is new or an update to an existing one.

The samples in an interval must be ordered by increasing time within a single packet.  Across packets, however, it is not necessary for the samples to be provided in any particular order.  However, care must be taken to ensure reasonable interpolation when streaming non-contiguous samples.

Consider a property that has sampled values at times 0.0 through 10.0, inclusive, at 1.0 second intervals.  The first packet contains times 0.0 through 3.0 and the second contains times 8.0 through 10.0.  The client has not yet received the third packet containing times 4.0 through 7.0.  Can we render the scene at time 5.0?

One approach is to interpolate across the two packets.  This is probably a bad idea, though, because interpolating across this gap can result in a very wrong-looking scene, especially with higher-degree interpolation.  So really, we'd like to pause animation, display some sort of "Buffering..." message to the user, and wait for the gap to be filled.  But how do we even know there's a gap?  We might infer that there's a gap because we have 1.0 second steps, and then a 5.0 second gap, and then 1.0 second gaps again.  But that's not reliable; maybe the object was just moving more slowly over that interval so we needed fewer samples.

CZML offers a solution in the form of two additional sub-properties for use with time-tagged samples: `previousTime` and `nextTime`.

```javascript
{  
    // ...  
    "someInterpolatableProperty": {  
        "epoch": "2012-04-30T12:00:00Z",  
        "cartesian": [  
            0.0, 1.0, 2.0, 3.0,  
            1.0, 4.0, 5.0, 6.0,  
            2.0, 7.0, 8.0, 9.0,
            3.0, 10.0, 11.0, 12.0
        ],  
        "previousTime": -1.0,  
        "nextTime": 4.0  
    }  
}
```

These properties tell the CZML client that the next sample time after 3.0 is 4.0.  If the next sample it has after 3.0 is 8.0, as in our example above, the client knows that there's a gap, and it will wait for more data before interpolating at a time within that gap.  