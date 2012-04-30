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

There are many standard properties defined for CZML, specifying how points, billboards, models, lines, and other graphics are added to the scene.  The available properties are described in detail on the [[CZML Content]] page.  On this page, we are primarily concerned with how the data is structured.  For example, we describe how a property can be specified such that it has two different values over two different intervals of time.
