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

In addition to the `id`, packets contain zero or more (but usually one or more) properties defining the graphical characteristics of the object.  In the example above, we've specified that the "GroundControlStation" object has a fixed position in Pennsylvania and that a blue dot is drawn at its location.

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

Here we define the "someProperty" property over two intervals, the first from noon to 1:00 PM UTC where the value of the property is 5, and the other from 1:00 PM to 2:00 PM UTC where the value of the property is 6.  We use `number` to indicate the value because this is a number-type property.  Some properties, notably properties that indicate position, allow the value to be specified in multiple formats, such as a Cartesian X,Y,Z position or a Cartographic longitude, latitude, height position.  The [[CZML Content]] page lists the types of data supported for each property, and the value names to use with each.

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

## Composite Values

## Sampled Property Values

## EventSource and Streaming

