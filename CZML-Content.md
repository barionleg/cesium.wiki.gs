This page describes the possible content of a CZML document or stream.  Please read [[CZML Structure]] for an explanation of how a CZML document is put together.

_NOTE: This is a work in progress and reflects our plans NOT our current capabilities._

## Id

The ID of the object described by this packet.  IDs do not need to be GUIDs, but they do need to uniquely identify a single object within a CZML source and any other CZML sources loaded into the same scope.  If this property is not specified, the client will automatically generate a unique one.  However, this prevents later packets from referring to this object in order to, for example, add more data to it.

**Property Name**: `id`

**Interpolatable**: no

## Availability

Indicates when data for an object is available. If data for an object is known to be available at the current animation time, but the client does not yet have that data (presumably because it will arrive in a later packet), the client will pause with a message like "Buffering..." while it waits to receive the data. The property can be a single string specifying a single interval, or an array of strings representing intervals.  A later Cesium packet can update this availability if it changes or is found to be incorrect. For example, an SGP4 propagator may report availability for all time, but then later the propagator throws an exception and the availability needs to be adjusted. If this optional property is not present, the object is assumed to be available for all time. Availability is scoped to a particular CZML stream, so two different streams can list different availability for a single object. Within a single stream, the last availability stated for an object is the one in effect and any availabilities in previous packets are ignored. If an object is available at a time, the client expects the object to have at least one property, and it expects all properties that it needs to be defined at that time. If the object doesn't have any properties, or a needed property is defined but not at the animation time, the client will pause animation and wait for more data.

**Property Name**: `availability`

**Interpolatable**: no

## Position

Specifies the position of the object in the world. The position has no direct visual representation, but it is used to locate billboards, labels, and other primitives attached to the object.

**Property Name**: `position`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `referenceFrame` | Interval | string | The reference frame in which cartesian positions are specified. Possible values are "FIXED" and "INERTIAL". In addition, the value of this property can be a hash (#) symbol followed by the ID of another object in the same scope whose "position" and "orientation" properties define the reference frame in which this position is defined.  This property is ignored when specifying position with any type other than cartesian. If this property is not specified, the default reference frame is "FIXED". |
| `cartesian` | Interval | array | The position specified as a Cartesian `[X, Y, Z]` position in the meters relative to the referenceFrame. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where Time is an ISO 8601 date and time string or seconds since epoch. |
| `cartographicRadians` | Interval | array | The position specified as a WGS 84 Cartographic `[Longitude, Latitude, Height]` where longitude and latitude are in radians and height is in meters. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, Longitude, Latitude, Height, Time, Longitude, Latitude, Height, ...]`, where Time is an ISO 8601 date and time string or seconds since epoch. |
| `cartographicDegrees` | Interval | array | The position specified as a WGS 84 Cartographic `[Longitude, Latitude, Height]` where longitude and latitude are in degrees and height is in meters. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, Longitude, Latitude, Height, Time, Longitude, Latitude, Height, ...]`, where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

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
    ],
    "nextTime", 300.0,
    "interpolationAlgorithm", "LAGRANGE",
    "interpolationDegree", 5
  }
}
```

## Billboard

Specifies a billboard, or viewport-aligned image. The billboard is positioned in the scene by the position property. A billboard is sometimes called a marker.

**Property Name**: `billboard`

**Interpolatable**: no

### Billboard.Color

The color of the billboard.  This color value is multiplied with the values of the billboard's "image" to produce the final color.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Billboard.EyeOffset

The eye offset of the billboard, which is the offset in eye coordinates at which to place the billboard relative to the `position` property.  Eye coordinates are a left-handed coordinate system where the X-axis points toward the viewer's right, the Y-axis poitns up, and the Z-axis points into the screen.

**Property Name**: `eyeOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian` | Interval | array | The eye offset specified as a Cartesian `[X, Y, Z]` position in eye coordinates in  meters.  If the array has three elements, the eye offset is constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


## Vertex Positions

Specifies the world-space positions of vertices.  The vertex positions have no direct visual representation, but they are used to define polygons, polylines, and other objects attached to the object.

**Property Name**: `Vertex Positions`

**Interpolatable**: no

## Orientation

Specifies the orientation of the object in the world.  The orientation has no direct visual representation, but it is used to orient models, cones, and pyramids attached to the object.

**Property Name**: `orientation`

**Interpolatable**: no

## Point

Defines a point, or viewport-aligned circle.  The point is positioned in the scene by the `position` property.

**Property Name**: `point`

**Interpolatable**: no

## Label

Defines a string of text.  The label is positioned in the scene by the `position` property.

**Property Name**: `label`

**Interpolatable**: no

## Polyline

Defines a polyline, which is a line in the scene composed of multiple segments.  The vertices of the polyline are specified by the `vertexPositions` property.

**Property Name**: `polyline`

**Interpolatable**: no

## Path

Defines a path, which is a polyline defined by the motion of an object over time.  The possible vertices of the path are specified by the `position` property.

**Property Name**: `path`

**Interpolatable**: no

## Polygon

Defines a polygon, which is a closed figure on the surface of the Earth.  The vertices of the polygon are specified by the `vertexPositions` property.

**Property Name**: `polygon`

**Interpolatable**: no

## Cone

Defines a cone.  A cone starts at a point or apex and extends in a circle of directions which all have the same angular separation from the Z-axis of the object to which the cone is attached.  The cone may be capped at a radial limit, it may have an inner hole, and it may be only a part of a complete cone defined by clock angle limits.  The apex point of the cone is defined by the `position` property and extends in the direction of the Z-axis as defined by the `orientation` property.

**Property Name**: `cone`

**Interpolatable**: no

## Pyramid

Defines a pyramid.  A pyramid starts at a point or apex and extends in a specified list of directions from the apex.  Each pair of directions forms a face of the pyramid.  The pyramid may be capped at a radial limit.

**Property Name**: `pyramid`

**Interpolatable**: no

