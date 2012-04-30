CZML is a subset of [JSON](http://www.json.org), meaning that a valid CZML document is also a valid JSON document.  Specifically, a CZML document contains a single JSON array where each object-literal element in the array is a CZML packet.  A CZML packet describes the graphical properties for a single object in the scene, such as a single aircraft.

_Note: we use javascript comments in these examples even though comments are not technically allowed in JSON._

```javascript
[
    {
        // packet one
        "id": "PredatorUAV",
        // ...
    },
    {
        // packet one
        "id": "GroundControlStation"
        // ...
    }
]
```

Each packet has an `id` property identifying the object is is describing.  IDs do not need to be GUIDs - URIs make good IDs - but they do need to uniquely identify a single object within a CZML source and any other CZML sources loaded into the same scope. We'll talk more about scopes later in this document.

If an `id` is not specified, the client will automatically generate a unique one. This prevents later packets from adding additional properties to the object. Also, other packets will not be able to reference the data in this one.

