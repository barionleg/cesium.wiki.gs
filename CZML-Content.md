This page describes the possible content of a CZML document or stream.  Please read [[CZML Structure]] for an explanation of how a CZML document is put together.

_NOTE: This is a work in progress and reflects our plans NOT our current capabilities._

## Id

The ID of the object described by this packet.  IDs do not need to be GUIDs, but they do need to uniquely identify a single object within a CZML source and any other CZML sources loaded into the same scope.  If this property is not specified, the client will automatically generate a unique one.  However, this prevents later packets from referring to this object in order to, for example, add more data to it.

**Property Name**: `id`

**Interpolatable**: no

## Name

The name of the object.  It does not have to be unique and is intended for user consumption.

**Property Name**: `name`

**Interpolatable**: no

## Parent

The ID of the parent object or folder.

**Property Name**: `parent`

**Interpolatable**: no

## Description

An HTML description of the object.

**Property Name**: `description`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `string` | Interval | string | The string value. |

## Availability

When data for an object is available. If data for an object is known to be available at the current animation time, but the client does not yet have that data (presumably because it will arrive in a later packet), the client will pause with a message like "Buffering..." while it waits to receive the data. The property can be a single string specifying a single interval, or an array of strings representing intervals.  A later Cesium packet can update this availability if it changes or is found to be incorrect. For example, an SGP4 propagator may report availability for all time, but then later the propagator throws an exception and the availability needs to be adjusted. If this optional property is not present, the object is assumed to be available for all time. Availability is scoped to a particular CZML stream, so two different streams can list different availability for a single object. Within a single stream, the last availability stated for an object is the one in effect and any availabilities in previous packets are ignored. If an object is available at a time, the client expects the object to have at least one property, and it expects all properties that it needs to be defined at that time. If the object doesn't have any properties, or a needed property is defined but not at the animation time, the client will pause animation and wait for more data.

**Property Name**: `availability`

**Interpolatable**: no

## Position

The position of the object in the world. The position has no direct visual representation, but it is used to locate billboards, labels, and other primitives attached to the object.

**Property Name**: `position`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `referenceFrame` | Interval | string | The reference frame in which cartesian positions are specified. Possible values are "FIXED" and "INERTIAL". In addition, the value of this property can be a hash (#) symbol followed by the ID of another object in the same scope whose "position" and "orientation" properties define the reference frame in which this position is defined.  This property is ignored when specifying position with any type other than cartesian. If this property is not specified, the default reference frame is "FIXED". |
| `cartesian` | Interval | array | The position represented as a Cartesian `[X, Y, Z]` in the meters relative to the `referenceFrame`. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where Time is an ISO 8601 date and time string or seconds since `epoch`. |
| `cartographicRadians` | Interval | array | The position represented as a WGS 84 Cartographic `[Longitude, Latitude, Height]` where longitude and latitude are in radians and height is in meters. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, Longitude, Latitude, Height, Time, Longitude, Latitude, Height, ...]`, where Time is an ISO 8601 date and time string or seconds since `epoch`. |
| `cartographicDegrees` | Interval | array | The position reprsented as a WGS 84 Cartographic `[Longitude, Latitude, Height]` where longitude and latitude are in degrees and height is in meters. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, Longitude, Latitude, Height, Time, Longitude, Latitude, Height, ...]`, where Time is an ISO 8601 date and time string or seconds since `epoch`. |
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
      240.0, -6654518.44949696, 52891.726433174, -1283967.69137678
    ],
    "nextTime": 300.0,
    "interpolationAlgorithm": "LAGRANGE",
    "interpolationDegree": 5
  }
}
```

## Billboard

A billboard, or viewport-aligned image. The billboard is positioned in the scene by the position property. A billboard is sometimes called a marker.

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

The eye offset of the billboard, which is the offset in eye coordinates at which to place the billboard relative to the `position` property.  Eye coordinates are a left-handed coordinate system where the X-axis points toward the viewer's right, the Y-axis points up, and the Z-axis points into the screen.

**Property Name**: `eyeOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian` | Interval | array | The eye offset specified as a Cartesian `[X, Y, Z]` position in eye coordinates in  meters.  If the array has three elements, the eye offset is constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Billboard.HorizontalOrigin

The horizontal origin of the billboard.  It controls whether the billboard image is left-, center-, or right-aligned with the `position`.

**Property Name**: `horizontalOrigin`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `horizontalOrigin` | Interval | string | The horizontal origin.  Valid values are "LEFT", "CENTER", and "RIGHT". |

### Billboard.Image

The image displayed on the billboard, expressed as a URL.  For broadest client compatibility, the URL should be accessible via Cross-Origin Resource Sharing (CORS).  The URL may also be a <a href="https://developer.mozilla.org/en/data_URIs">data URI</a>.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |

### Billboard.PixelOffset

The offset, in viewport pixels, of the billboard origin from the `position`.  A pixel offset is the number of pixels up and to the right to place the billboard, relative to the `position`.

**Property Name**: `pixelOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The pixel offset specified as a Cartesian `[X, Y]` in viewport coordinates in pixels, where X is pixels to the right and Y is pixels up.  If the array has two elements, the pixel offset is constant.  If it has three or more elements, they are time-tagged samples arranged as `[Time, X, Y, Time, X, Y, Time, X, Y, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Billboard.Scale

The scale of the billboard.  The scale is multiplied with the pixel size of the billboard's `image`.  For example, if the scale is 2.0, the billboard will be rendered with twice the number of pixels, in each direction, of the `image`.

**Property Name**: `scale`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Billboard.Rotation

The rotation of the billboard offset from the alignedAxes.

**Property Name**: `rotation`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Billboard.AlignedAxis

The aligned axis is the unit vector, in world coordinates, that the billboard up vector points towards. The default is the zero vector, which means the billboard is aligned to the screen up vector.

**Property Name**: `alignedAxis`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian` | Interval | array | The axis specified as a unit Cartesian `[X, Y, Z]` in world coordinates in  meters.  If the array has three elements, the eye offset is constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Billboard.Show

Whether or not the billboard is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Billboard.VerticalOrigin

The vertical origin of the billboard.  It controls whether the billboard image is bottom-, center-, or top-aligned with the `position`.

**Property Name**: `verticalOrigin`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `verticalOrigin` | Interval | string | The vertical origin.  Valid values are "BOTTOM", "CENTER", and "TOP". |


## VertexPositions

The world-space positions of vertices.  The vertex positions have no direct visual representation, but they are used to define polygons, polylines, and other objects attached to the object.

**Property Name**: `vertexPositions`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `referenceFrame` | Interval | string | The reference frame in which cartesian positions are specified. Possible values are "FIXED" and "INERTIAL". In addition, the value of this property can be a hash (#) symbol followed by the ID of another object in the same scope whose "position" and "orientation" properties define the reference frame in which this position is defined.  This property is ignored when specifying position with any type other than cartesian. If this property is not specified, the default reference frame is "FIXED". |
| `cartesian` | Interval | array | The list of positions represented as Cartesian `[X, Y, Z, X, Y, Z, ...]` in the meters relative to the `referenceFrame`. |
| `cartographicRadians` | Interval | array | The list of positions represented as WGS 84 `[Longitude, Latitude, Height, Longitude, Latitude, Height, ...]` where longitude and latitude are in radians and height is in meters. |
| `cartographicDegrees` | Interval | array | The list of positions represented as WGS 84 `[Longitude, Latitude, Height, Longitude, Latitude, Height, ...]` where longitude and latitude are in degrees and height is in meters. |
| `references` | Interval | array | The list of positions specified as references.  Each reference is to a property that defines a single position, possible as it changes with time. |

## Orientation

The orientation of the object in the world.  The orientation has no direct visual representation, but it is used to orient models, cones, and pyramids attached to the object.

**Property Name**: `orientation`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `axes` | Interval | string | TODO |
| `unitQuaternion` | Interval | array | TODO |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

## Point

A point, or viewport-aligned circle.  The point is positioned in the scene by the `position` property.

**Property Name**: `point`

**Interpolatable**: no

### Point.Color

The color of the point.

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

### Point.OutlineColor

The color of the outline of the point.

**Property Name**: `outlineColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Point.OutlineWidth

The width of the outline of the point.

**Property Name**: `outlineWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Point.PixelSize

The size of the point, in pixels.

**Property Name**: `pixelSize`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Point.Show

Whether or not the point is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |


## Label

A string of text.  The label is positioned in the scene by the `position` property.

**Property Name**: `label`

**Interpolatable**: no

### Label.EyeOffset

The eye offset of the label, which is the offset in eye coordinates at which to place the label relative to the `position` property.  Eye coordinates are a left-handed coordinate system where the X-axis points toward the viewer's right, the Y-axis points up, and the Z-axis points into the screen.

**Property Name**: `eyeOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian` | Interval | array | The eye offset specified as a Cartesian `[X, Y, Z]` position in eye coordinates in  meters.  If the array has three elements, the eye offset is constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Label.FillColor

The fill color of the label.

**Property Name**: `fillColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Label.Font

The font to use for the label.

**Property Name**: `font`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `font` | Interval | string | The font. |

### Label.HorizontalOrigin

The horizontal origin of the label.  It controls whether the label is left-, center-, or right-aligned with the `position`.

**Property Name**: `horizontalOrigin`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `horizontalOrigin` | Interval | string | The horizontal origin.  Valid values are "LEFT", "CENTER", and "RIGHT". |

### Label.OutlineColor

The outline color of the label.

**Property Name**: `outlineColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Label.OutlineWidth

The outline width of the label.

**Property Name**: `outlineWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Label.PixelOffset

The offset, in viewport pixels, of the label origin from the `position`.  A pixel offset is the number of pixels up and to the right to place the label, relative to the `position`.

**Property Name**: `pixelOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The pixel offset specified as a Cartesian `[X, Y]` in viewport coordinates in pixels, where X is pixels to the right and Y is pixels up.  If the array has two elements, the pixel offset is constant.  If it has three or more elements, they are time-tagged samples arranged as `[Time, X, Y, Time, X, Y, Time, X, Y, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Label.Scale

The scale of the label.  The scale is multiplied with the pixel size of the label's text.  For example, if the scale is 2.0, the label will be rendered with twice the number of pixels, in each direction, of the text.

**Property Name**: `scale`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Label.Show

Whether or not the label is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Label.Style

The style of the label.

**Property Name**: `style`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `labelStyle` | Interval | string | The label style.  Valid values are "FILL", "OUTLINE", and "FILL_AND_OUTLINE". |

### Label.Text

The text displayed by the label.

**Property Name**: `text`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `string` | Interval | string | The string value. |

### Label.VerticalOrigin

The vertical origin of the label.  It controls whether the label image is bottom-, center-, or top-aligned with the `position`.

**Property Name**: `verticalOrigin`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `verticalOrigin` | Interval | string | The vertical origin.  Valid values are "BOTTOM", "CENTER", and "TOP". |


## Polyline

A polyline, which is a line in the scene composed of multiple segments.  The vertices of the polyline are specified by the `vertexPositions` property.

**Property Name**: `polyline`

**Interpolatable**: no

### Polyline.Show

Whether or not the polyline is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Polyline.Color

The color of the polyline.

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

### Polyline.Width

The width of the polyline.

**Property Name**: `width`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Polyline.OutlineColor

The color of the outline of the polyline.

**Property Name**: `outlineColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Polyline.OutlineWidth

The width of the outline of the polyline.

**Property Name**: `outlineWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


## Path

A path, which is a polyline defined by the motion of an object over time.  The possible vertices of the path are specified by the `position` property.

**Property Name**: `path`

**Interpolatable**: no

### Path.Show

Whether or not the path is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Path.Color

The color of the path line.

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

### Path.Width

The width of the path line.

**Property Name**: `width`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Path.Resolution

The maximum step-size, in seconds, used to sample the path.  If the `position` property has data points farther apart than resolution specfies, additional steps will be taken, creating a smoother path.

**Property Name**: `resolution`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Path.OutlineColor

The color of the outline of the path.

**Property Name**: `outlineColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Path.OutlineWidth

The width of the outline of the path.

**Property Name**: `outlineWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Path.LeadTime

The time ahead of the animation time, in seconds, to show the path.

**Property Name**: `leadTime`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Path.TrailTime

The time behind the animation time, in seconds, to show the path.

**Property Name**: `trailTime`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


## Polygon

A polygon, which is a closed figure on the surface of the Earth.  The vertices of the polygon are specified by the `vertexPositions` property.

**Property Name**: `polygon`

**Interpolatable**: no

### Polygon.Show

Whether or not the billboard is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Polygon.Material

The material to use to fill the polygon.

**Property Name**: `material`

**Interpolatable**: no

#### Polygon.Material.SolidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### Polygon.Material.SolidColor.Color

The color of the surface.

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


#### Polygon.Material.Image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### Polygon.Material.Image.Image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |


#### Polygon.Material.Grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### Polygon.Material.Grid.Color

The color of the surface.

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

##### Polygon.Material.Grid.CellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Polygon.Material.Grid.RowCount

The number of horizontal grid lines.

**Property Name**: `rowCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Polygon.Material.Grid.ColumnCount

The number of vertical grid lines.

**Property Name**: `columnCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Polygon.Material.Grid.RowThickness

The thickness of horizontal grid lines, in pixels.

**Property Name**: `rowThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Polygon.Material.Grid.ColumnThickness

The thickness of vertical grid lines, in pixels.

**Property Name**: `columnThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |




## Cone

A cone.  A cone starts at a point or apex and extends in a circle of directions which all have the same angular separation from the Z-axis of the object to which the cone is attached.  The cone may be capped at a radial limit, it may have an inner hole, and it may be only a part of a complete cone defined by clock angle limits.  The apex point of the cone is defined by the `position` property and extends in the direction of the Z-axis as defined by the `orientation` property.

**Property Name**: `cone`

**Interpolatable**: no

### Cone.Show

Whether or not the cone is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Cone.InnerHalfAngle

The inner half angle of the cone.

**Property Name**: `innerHalfAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Cone.OuterHalfAngle

The outer half angle of the cone.

**Property Name**: `outerHalfAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Cone.Radius

The radial limit of the cone.

**Property Name**: `radius`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Cone.MinimumClockAngle

The minimum clock angle limit of the cone.

**Property Name**: `minimumClockAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Cone.MaximumClockAngle

The maximum clock angle limit of the cone.

**Property Name**: `maximumClockAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Cone.ShowIntersection

Whether or not the intersection of the cone with the Earth is shown.

**Property Name**: `showIntersection`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Cone.IntersectionColor

The color of the intersection of the cone with the Earth.

**Property Name**: `intersectionColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Cone.IntersectionWidth

The width of the intersection in pixels.

**Property Name**: `intersectionWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Cone.CapMaterial

The material to use to cap the cone at its radial limit.

**Property Name**: `capMaterial`

**Interpolatable**: no

#### Cone.CapMaterial.SolidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### Cone.CapMaterial.SolidColor.Color

The color of the surface.

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


#### Cone.CapMaterial.Image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### Cone.CapMaterial.Image.Image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |


#### Cone.CapMaterial.Grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### Cone.CapMaterial.Grid.Color

The color of the surface.

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

##### Cone.CapMaterial.Grid.CellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.CapMaterial.Grid.RowCount

The number of horizontal grid lines.

**Property Name**: `rowCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.CapMaterial.Grid.ColumnCount

The number of vertical grid lines.

**Property Name**: `columnCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.CapMaterial.Grid.RowThickness

The thickness of horizontal grid lines, in pixels.

**Property Name**: `rowThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.CapMaterial.Grid.ColumnThickness

The thickness of vertical grid lines, in pixels.

**Property Name**: `columnThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### Cone.InnerMaterial

The material to use for the inner cone.

**Property Name**: `innerMaterial`

**Interpolatable**: no

#### Cone.InnerMaterial.SolidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### Cone.InnerMaterial.SolidColor.Color

The color of the surface.

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


#### Cone.InnerMaterial.Image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### Cone.InnerMaterial.Image.Image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |


#### Cone.InnerMaterial.Grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### Cone.InnerMaterial.Grid.Color

The color of the surface.

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

##### Cone.InnerMaterial.Grid.CellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.InnerMaterial.Grid.RowCount

The number of horizontal grid lines.

**Property Name**: `rowCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.InnerMaterial.Grid.ColumnCount

The number of vertical grid lines.

**Property Name**: `columnCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.InnerMaterial.Grid.RowThickness

The thickness of horizontal grid lines, in pixels.

**Property Name**: `rowThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.InnerMaterial.Grid.ColumnThickness

The thickness of vertical grid lines, in pixels.

**Property Name**: `columnThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### Cone.OuterMaterial

The material to use for the outer cone.

**Property Name**: `outerMaterial`

**Interpolatable**: no

#### Cone.OuterMaterial.SolidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### Cone.OuterMaterial.SolidColor.Color

The color of the surface.

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


#### Cone.OuterMaterial.Image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### Cone.OuterMaterial.Image.Image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |


#### Cone.OuterMaterial.Grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### Cone.OuterMaterial.Grid.Color

The color of the surface.

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

##### Cone.OuterMaterial.Grid.CellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.OuterMaterial.Grid.RowCount

The number of horizontal grid lines.

**Property Name**: `rowCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.OuterMaterial.Grid.ColumnCount

The number of vertical grid lines.

**Property Name**: `columnCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.OuterMaterial.Grid.RowThickness

The thickness of horizontal grid lines, in pixels.

**Property Name**: `rowThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.OuterMaterial.Grid.ColumnThickness

The thickness of vertical grid lines, in pixels.

**Property Name**: `columnThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### Cone.SilhouetteMaterial

The material to use for the cone's silhouette.

**Property Name**: `silhouetteMaterial`

**Interpolatable**: no

#### Cone.SilhouetteMaterial.SolidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### Cone.SilhouetteMaterial.SolidColor.Color

The color of the surface.

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


#### Cone.SilhouetteMaterial.Image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### Cone.SilhouetteMaterial.Image.Image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |


#### Cone.SilhouetteMaterial.Grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### Cone.SilhouetteMaterial.Grid.Color

The color of the surface.

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

##### Cone.SilhouetteMaterial.Grid.CellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.SilhouetteMaterial.Grid.RowCount

The number of horizontal grid lines.

**Property Name**: `rowCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.SilhouetteMaterial.Grid.ColumnCount

The number of vertical grid lines.

**Property Name**: `columnCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.SilhouetteMaterial.Grid.RowThickness

The thickness of horizontal grid lines, in pixels.

**Property Name**: `rowThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Cone.SilhouetteMaterial.Grid.ColumnThickness

The thickness of vertical grid lines, in pixels.

**Property Name**: `columnThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |




## Pyramid

A pyramid.  A pyramid starts at a point or apex and extends in a specified list of directions from the apex.  Each pair of directions forms a face of the pyramid.  The pyramid may be capped at a radial limit.

**Property Name**: `pyramid`

**Interpolatable**: no

### Pyramid.Show

Whether or not the pyramid is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Pyramid.Directions

The list of directions defining the pyramid.

**Property Name**: `directions`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `unitSpherical` | Interval | array | The list of directions represented as a clock angle and a cone angle, both in radians.  The clock angle is measured in the XY plane from the positive X axis toward the positive Y axis.  The cone angle is the angle from the positive Z axis toward the negative Z axis. |
| `unitCartesian` | Interval | array | The list of directions represented as Cartesian `[X, Y, Z, X, Y, Z, ...]`. |

### Pyramid.Radius

The radial limit of the pyramid.

**Property Name**: `radius`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Pyramid.ShowIntersection

Whether or not the intersection of the pyramid with the Earth is shown.

**Property Name**: `showIntersection`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Pyramid.IntersectionColor

The color of the intersection of the pyramid with the Earth.

**Property Name**: `intersectionColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Pyramid.IntersectionWidth

The width of the intersection in pixels.

**Property Name**: `intersectionWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Pyramid.Material

The material to display on the surface of the pyramid.

**Property Name**: `material`

**Interpolatable**: no

#### Pyramid.Material.SolidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### Pyramid.Material.SolidColor.Color

The color of the surface.

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


#### Pyramid.Material.Image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### Pyramid.Material.Image.Image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |


#### Pyramid.Material.Grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### Pyramid.Material.Grid.Color

The color of the surface.

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

##### Pyramid.Material.Grid.CellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Pyramid.Material.Grid.RowCount

The number of horizontal grid lines.

**Property Name**: `rowCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Pyramid.Material.Grid.ColumnCount

The number of vertical grid lines.

**Property Name**: `columnCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Pyramid.Material.Grid.RowThickness

The thickness of horizontal grid lines, in pixels.

**Property Name**: `rowThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Pyramid.Material.Grid.ColumnThickness

The thickness of vertical grid lines, in pixels.

**Property Name**: `columnThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |




## Camera

A camera.

**Property Name**: `camera`

**Interpolatable**: no

### Camera.Enable

Whether or not the camera is enabled.

**Property Name**: `enable`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |


## Ellipsoid

An ellipsoid, which is a closed quadric surface that is a three dimensional analogue of an ellipse.  The ellipsoid is positioned and oriented using the `position` and `orientation` properties.

**Property Name**: `ellipsoid`

**Interpolatable**: no

### Ellipsoid.Show

Whether or not the ellipsoid is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Ellipsoid.Radii

The dimensions of the ellipsoid.

**Property Name**: `radii`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian` | Interval | array | The radii as a Cartesian `[X, Y, Z]` in meters. If the array has three elements, the radii are constant.  If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where _Time_ is an ISO 8601 date and time string or seconds since `epoch`. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Ellipsoid.Material

The material to display on the surface of the ellipsoid.

**Property Name**: `material`

**Interpolatable**: no

#### Ellipsoid.Material.SolidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### Ellipsoid.Material.SolidColor.Color

The color of the surface.

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


#### Ellipsoid.Material.Image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### Ellipsoid.Material.Image.Image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `image` | Interval | string | The URL of the image. |


#### Ellipsoid.Material.Grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### Ellipsoid.Material.Grid.Color

The color of the surface.

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

##### Ellipsoid.Material.Grid.CellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Ellipsoid.Material.Grid.RowCount

The number of horizontal grid lines.

**Property Name**: `rowCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Ellipsoid.Material.Grid.ColumnCount

The number of vertical grid lines.

**Property Name**: `columnCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Ellipsoid.Material.Grid.RowThickness

The thickness of horizontal grid lines, in pixels.

**Property Name**: `rowThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### Ellipsoid.Material.Grid.ColumnThickness

The thickness of vertical grid lines, in pixels.

**Property Name**: `columnThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |




## ViewFrom

A suggested camera location when viewing this object.  The property is specified as a Cartesian position in the East (x), North (y), Up (z) reference frame relative to the objects position property.

**Property Name**: `viewFrom`

**Interpolatable**: no

## Ellipse

An ellipse, which is a closed curve on the surface of the Earth.  The ellipse is positioned using the `position` property.

**Property Name**: `ellipse`

**Interpolatable**: no

### Ellipse.SemiMajorAxis

The length of the ellipse's semi-major axis in meters.

**Property Name**: `semiMajorAxis`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Ellipse.SemiMinorAxis

The length of the ellipse's semi-minor axis in meters.

**Property Name**: `semiMinorAxis`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Ellipse.Rotation

The angle from north (clockwise) in radians.

**Property Name**: `rotation`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


## Clock

A simulated clock.

**Property Name**: `clock`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `currentTime` | Interval | string | The current time. |
| `multiplier` | Interval | number | The multiplier, which in TICK_DEPENDENT mode is the number of seconds to advance each tick.  In SYSTEM_CLOCK_DEPENDENT mode, it is the multiplier applied to the amount of time elapsed between ticks.  This value is ignored in SYSTEM_CLOCK mode. |
| `range` | Interval | string | The behavior of a clock when its current time reaches its start or end points.  Valid values are 'UNBOUNDED', 'CLAMPED', and 'LOOP_STOP'. |
| `step` | Interval | string | Defines how a clock steps in time.  Valid values are 'SYSTEM_CLOCK', 'SYSTEM_CLOCK_MULTIPLIER', and 'TICK_DEPENDENT'. |

## Vector

Defines a graphical vector that originates at the `position` property and extends in the provided direction for the provided length.

**Property Name**: `vector`

**Interpolatable**: no

### Vector.Show

Whether or not the vector is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### Vector.Color

The color of the vector.

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

### Vector.Width

The width of the vector.

**Property Name**: `width`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Vector.Direction

The direction of the vector.

**Property Name**: `direction`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `axes` | Interval | string | TODO |
| `unitCartesian` | Interval | array | The direction represented as a unit Cartesian `[X, Y, Z]`. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where Time is an ISO 8601 date and time string or seconds since `epoch`. |
| `unitSpherical` | Interval | array | A direction specified as a unit spherical [Clock, Cone] angles in radians. If the array has two elements, the direction is constant. If it has three or more elements, they are time-tagged samples arranged as [Time, Clock, Cone, Time, Clock, Cone, Time, Clock, Cone, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### Vector.Length

The graphical length of the vector.

**Property Name**: `length`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


