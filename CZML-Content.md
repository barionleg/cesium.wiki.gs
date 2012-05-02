This page describes the possible content of a CZML document or stream.  Please read [[CZML Structure]] for an explanation of how a CZML document is put together.

## Position

Specifies the position of the object in the world.  The position has no direct visual representation, but it is used to locate billboards, labels, and other primitives attached to the object.

**Property Name**: `position`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | JSON | Description |
|:-----|:------|:-----|:------------|
| `referenceFrame` | Interval | string | The reference frame in which `cartesian` positions are specified.  Possible values are `FIXED` and `INERTIAL`.  This property is ignored when specifying position with any type other than `cartesian`.  If this property is not specified, the default reference frame is `FIXED`. |
| `epoch` | Packet | string | The epoch (time 0.0), specified as an [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) date and time string, for times specified in epoch seconds.  This property is required if a sample time or other property is specified in epoch seconds.  It is ignored if this property is not defined by samples for this interval. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since `epoch`.  This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since `epoch`.  This property is used to determine if there is a gap between samples specified in different packets. |
| `cartesian` | Interval | array | The position specified as a Cartesian `[X, Y, Z]` position in the meters relative to the `referenceFrame`.  If the array has three elements, the position is constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `cartographicRadians` | Interval | array | The position specified as a [WGS 84](http://en.wikipedia.org/wiki/World_Geodetic_System) Cartographic `[Longitude, Latitude, Height]` where longitude and latitude are in radians and height is in meters.  If the array has three elements, the position is constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, Longitude, Latitude, Height, Time, Longitude, Latitude, Height, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `cartographicDegrees` | Interval | array | The position specified as a [WGS 84](http://en.wikipedia.org/wiki/World_Geodetic_System) Cartographic `[Longitude, Latitude, Height]` where longitude and latitude are in degrees and height is in meters.  If the array has three elements, the position is constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, Longitude, Latitude, Height, Time, Longitude, Latitude, Height, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `interpolationAlgorithm` | Interval | string | |
| `interpolationDegree` | Interval | number | |

Examples:

```javascript
{
  "id": "MyObject",
  "position": { "cartographicDegrees": [-75.0, 40.0, 0.0] }
}
```

```javascript
{
  "id": "InternationalSpaceStation",
  "position": {
    "referenceFrame": "INERTIAL",
    "epoch": "2012-05-02T12:00:00Z",
    "cartesian": [
      0.0, -6668447.2211117, 1201886.45913705, 146789.427467256,
      60.0, -6711432.84684144, 919677.673492462, -214047.552431458,
      90.0, -6721319.92231553, 776899.784034099, -394198.837519575,
      150.0, -6717826.447064, 488820.628328182, -752924.980158179,
      180.0, -6704450.41462847, 343851.784836767, -931084.800346031,
      240.0, -6654518.44949696, 52891.726433174, -1283967.69137678,
    ]
  }
}

## Orientation

## Billboard

## Point

## Label

## Polyline

## Path

## Polygon

## Cone

## Pyramid

## Imagery

## Layers