## Part II

(Also see CZML Content [Part I](https://github.com/AnalyticalGraphicsInc/cesium/wiki/CZML-Content))

## agi_conicSensor

A conical sensor volume taking into account occlusion of an ellipsoid, i.e., the globe.

_Note: This type is an extension and may not be implemented by all CZML clients._

**Property Name**: `agi_conicSensor`

**Interpolatable**: no

### agi_conicSensor.show

Whether or not the cone is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_conicSensor.innerHalfAngle

The inner half angle of the cone.

**Property Name**: `innerHalfAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_conicSensor.outerHalfAngle

The outer half angle of the cone.

**Property Name**: `outerHalfAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_conicSensor.minimumClockAngle

The minimum clock angle limit of the cone.

**Property Name**: `minimumClockAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_conicSensor.maximumClockAngle

The maximum clock angle limit of the cone.

**Property Name**: `maximumClockAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_conicSensor.radius

The radial limit of the cone.

**Property Name**: `radius`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_conicSensor.showIntersection

Whether or not the intersection of the cone with the Earth is shown.

**Property Name**: `showIntersection`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_conicSensor.intersectionColor

The color of the intersection of the cone with the Earth.

**Property Name**: `intersectionColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_conicSensor.intersectionWidth

The width of the intersection in pixels.

**Property Name**: `intersectionWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_conicSensor.showLateralSurfaces

Whether or not the intersections of the cone with the earth are shown.

**Property Name**: `showLateralSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_conicSensor.lateralSurfaceMaterial

Whether or not lateral surfaces are shown.

**Property Name**: `lateralSurfaceMaterial`

**Interpolatable**: no

#### agi_conicSensor.lateralSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_conicSensor.lateralSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.lateralSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_conicSensor.lateralSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.lateralSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.lateralSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_conicSensor.lateralSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.lateralSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.lateralSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.lateralSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.lateralSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.lateralSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_conicSensor.lateralSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.lateralSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.lateralSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.lateralSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.lateralSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_conicSensor.showEllipsoidSurfaces

Whether or not ellipsoid surfaces are shown.

**Property Name**: `showEllipsoidSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_conicSensor.ellipsoidSurfaceMaterial

The material to use for the cone's ellipsoid surface.

**Property Name**: `ellipsoidSurfaceMaterial`

**Interpolatable**: no

#### agi_conicSensor.ellipsoidSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.ellipsoidSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.ellipsoidSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.ellipsoidSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_conicSensor.showEllipsoidHorizonSurfaces

Whether or not ellipsoid horizon surfaces are shown.

**Property Name**: `showEllipsoidHorizonSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_conicSensor.ellipsoidHorizonSurfaceMaterial

The material to use for the cone's ellipsoid horizon surface.

**Property Name**: `ellipsoidHorizonSurfaceMaterial`

**Interpolatable**: no

#### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.ellipsoidHorizonSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_conicSensor.showDomeSurfaces

Whether or not dome surfaces are shown.

**Property Name**: `showDomeSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_conicSensor.domeSurfaceMaterial

The material to use for the cone's dome.

**Property Name**: `domeSurfaceMaterial`

**Interpolatable**: no

#### agi_conicSensor.domeSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_conicSensor.domeSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.domeSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_conicSensor.domeSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.domeSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.domeSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_conicSensor.domeSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.domeSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.domeSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.domeSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.domeSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_conicSensor.domeSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_conicSensor.domeSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_conicSensor.domeSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.domeSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.domeSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_conicSensor.domeSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_conicSensor.portionToDisplay

Indicates what part of a sensor should be displayed.

**Property Name**: `portionToDisplay`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `portionToDisplay` | Interval | string | Indicates what part of a sensor should be displayed.  Valid values are "COMPLETE", "BELOW_ELLIPSOID_HORIZON", "ABOVE_ELLIPSOID_HORIZON". |
| `reference` | Interval | string | A reference property. |


## agi_customPatternSensor

A custom sensor volume taking into account occlusion of an ellipsoid, i.e., the globe.

_Note: This type is an extension and may not be implemented by all CZML clients._

**Property Name**: `agi_customPatternSensor`

**Interpolatable**: no

### agi_customPatternSensor.show

Whether or not the pyramid is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_customPatternSensor.directions

The list of directions defining the pyramid.

**Property Name**: `directions`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `spherical` | Interval | array | The list of directions represented as a clock angle, a cone angle, both in radians, and magnitude in meters.  The clock angle is measured in the XY plane from the positive X axis toward the positive Y axis.  The cone angle is the angle from the positive Z axis toward the negative Z axis. |
| `unitSpherical` | Interval | array | The list of directions represented as a clock angle and a cone angle, both in radians.  The clock angle is measured in the XY plane from the positive X axis toward the positive Y axis.  The cone angle is the angle from the positive Z axis toward the negative Z axis. |
| `cartesian` | Interval | array | The list of directions represented as Cartesian `[X, Y, Z, X, Y, Z, ...]` |
| `unitCartesian` | Interval | array | The list of directions represented as Cartesian `[X, Y, Z, X, Y, Z, ...]`. |

### agi_customPatternSensor.radius

The radial limit of the pyramid.

**Property Name**: `radius`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_customPatternSensor.showIntersection

Whether or not the intersection of the pyramid with the Earth is shown.

**Property Name**: `showIntersection`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_customPatternSensor.intersectionColor

The color of the intersection of the pyramid with the Earth.

**Property Name**: `intersectionColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_customPatternSensor.intersectionWidth

The width of the intersection in pixels.

**Property Name**: `intersectionWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_customPatternSensor.showLateralSurfaces

Whether or not the intersections of the pyramid with the earth are shown.

**Property Name**: `showLateralSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_customPatternSensor.lateralSurfaceMaterial

Whether or not lateral surfaces are shown.

**Property Name**: `lateralSurfaceMaterial`

**Interpolatable**: no

#### agi_customPatternSensor.lateralSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_customPatternSensor.lateralSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.lateralSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_customPatternSensor.lateralSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.lateralSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.lateralSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_customPatternSensor.lateralSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.lateralSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.lateralSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.lateralSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.lateralSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.lateralSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_customPatternSensor.lateralSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.lateralSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.lateralSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.lateralSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.lateralSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_customPatternSensor.showEllipsoidSurfaces

Whether or not ellipsoid surfaces are shown.

**Property Name**: `showEllipsoidSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_customPatternSensor.ellipsoidSurfaceMaterial

The material to use for the pyramid's ellipsoid surface.

**Property Name**: `ellipsoidSurfaceMaterial`

**Interpolatable**: no

#### agi_customPatternSensor.ellipsoidSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.ellipsoidSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.ellipsoidSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.ellipsoidSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_customPatternSensor.showEllipsoidHorizonSurfaces

Whether or not ellipsoid horizon surfaces are shown.

**Property Name**: `showEllipsoidHorizonSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial

The material to use for the pyramid's ellipsoid horizon surface.

**Property Name**: `ellipsoidHorizonSurfaceMaterial`

**Interpolatable**: no

#### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.ellipsoidHorizonSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_customPatternSensor.showDomeSurfaces

Whether or not dome surfaces are shown.

**Property Name**: `showDomeSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_customPatternSensor.domeSurfaceMaterial

The material to use for the pyramid's dome.

**Property Name**: `domeSurfaceMaterial`

**Interpolatable**: no

#### agi_customPatternSensor.domeSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_customPatternSensor.domeSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.domeSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_customPatternSensor.domeSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.domeSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.domeSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_customPatternSensor.domeSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.domeSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.domeSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.domeSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.domeSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_customPatternSensor.domeSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_customPatternSensor.domeSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_customPatternSensor.domeSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.domeSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.domeSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_customPatternSensor.domeSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_customPatternSensor.portionToDisplay

Indicates what part of a sensor should be displayed.

**Property Name**: `portionToDisplay`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `portionToDisplay` | Interval | string | Indicates what part of a sensor should be displayed.  Valid values are "COMPLETE", "BELOW_ELLIPSOID_HORIZON", "ABOVE_ELLIPSOID_HORIZON". |
| `reference` | Interval | string | A reference property. |


## agi_fan

Defines a fan, which starts at a point or apex and extends in a specified list of directions from the apex.  Each pair of directions forms a face of the fan extending to the specified radius.

_Note: This type is an extension and may not be implemented by all CZML clients._

**Property Name**: `agi_fan`

**Interpolatable**: no

### agi_fan.show

Whether or not the fan is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_fan.directions

The list of directions defining the fan.

**Property Name**: `directions`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `spherical` | Interval | array | The list of directions represented as a clock angle, a cone angle, both in radians, and magnitude in meters.  The clock angle is measured in the XY plane from the positive X axis toward the positive Y axis.  The cone angle is the angle from the positive Z axis toward the negative Z axis. |
| `unitSpherical` | Interval | array | The list of directions represented as a clock angle and a cone angle, both in radians.  The clock angle is measured in the XY plane from the positive X axis toward the positive Y axis.  The cone angle is the angle from the positive Z axis toward the negative Z axis. |
| `cartesian` | Interval | array | The list of directions represented as Cartesian `[X, Y, Z, X, Y, Z, ...]` |
| `unitCartesian` | Interval | array | The list of directions represented as Cartesian `[X, Y, Z, X, Y, Z, ...]`. |

### agi_fan.radius

The radial limit of the fan.

**Property Name**: `radius`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_fan.perDirectionRadius

When true, the magnitude of each direction is used instead of a constant radius.

**Property Name**: `perDirectionRadius`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_fan.material

The material to display on the surface of the fan.

**Property Name**: `material`

**Interpolatable**: no

#### agi_fan.material.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_fan.material.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_fan.material.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_fan.material.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_fan.material.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_fan.material.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_fan.material.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_fan.material.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_fan.material.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_fan.material.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_fan.material.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_fan.material.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_fan.material.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_fan.material.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_fan.material.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_fan.material.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_fan.material.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_fan.fill

Whether or not the fan is filled.

**Property Name**: `fill`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_fan.outline

Whether or not the fan is outlined.

**Property Name**: `outline`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_fan.numberOfRings

The number of outline rings to draw, starting from the outer edge and equidistantly spaced towards the center.

**Property Name**: `numberOfRings`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_fan.outlineColor

The color of the fan outline.

**Property Name**: `outlineColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


## agi_rectangularSensor

A rectangular pyramid sensor volume taking into account occlusion of an ellipsoid, i.e., the globe.

_Note: This type is an extension and may not be implemented by all CZML clients._

**Property Name**: `agi_rectangularSensor`

**Interpolatable**: no

### agi_rectangularSensor.show

Whether or not the pyramid is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_rectangularSensor.xHalfAngle

The X half angle.

**Property Name**: `xHalfAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_rectangularSensor.yHalfAngle

The Y half angle.

**Property Name**: `yHalfAngle`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_rectangularSensor.radius

The radial limit of the pyramid.

**Property Name**: `radius`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_rectangularSensor.showIntersection

Whether or not the intersection of the pyramid with the Earth is shown.

**Property Name**: `showIntersection`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_rectangularSensor.intersectionColor

The color of the intersection of the pyramid with the Earth.

**Property Name**: `intersectionColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_rectangularSensor.intersectionWidth

The width of the intersection in pixels.

**Property Name**: `intersectionWidth`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_rectangularSensor.showLateralSurfaces

Whether or not the intersections of the pyramid with the earth are shown.

**Property Name**: `showLateralSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_rectangularSensor.lateralSurfaceMaterial

Whether or not lateral surfaces are shown.

**Property Name**: `lateralSurfaceMaterial`

**Interpolatable**: no

#### agi_rectangularSensor.lateralSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_rectangularSensor.lateralSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.lateralSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_rectangularSensor.lateralSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.lateralSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.lateralSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_rectangularSensor.lateralSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.lateralSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.lateralSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.lateralSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.lateralSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.lateralSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_rectangularSensor.lateralSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.lateralSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.lateralSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.lateralSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.lateralSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_rectangularSensor.showEllipsoidSurfaces

Whether or not ellipsoid surfaces are shown.

**Property Name**: `showEllipsoidSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_rectangularSensor.ellipsoidSurfaceMaterial

The material to use for the pyramid's ellipsoid surface.

**Property Name**: `ellipsoidSurfaceMaterial`

**Interpolatable**: no

#### agi_rectangularSensor.ellipsoidSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.ellipsoidSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.ellipsoidSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.ellipsoidSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_rectangularSensor.showEllipsoidHorizonSurfaces

Whether or not ellipsoid horizon surfaces are shown.

**Property Name**: `showEllipsoidHorizonSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial

The material to use for the pyramid's ellipsoid horizon surface.

**Property Name**: `ellipsoidHorizonSurfaceMaterial`

**Interpolatable**: no

#### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.ellipsoidHorizonSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_rectangularSensor.showDomeSurfaces

Whether or not dome surfaces are shown.

**Property Name**: `showDomeSurfaces`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_rectangularSensor.domeSurfaceMaterial

The material to use for the pyramid's dome.

**Property Name**: `domeSurfaceMaterial`

**Interpolatable**: no

#### agi_rectangularSensor.domeSurfaceMaterial.solidColor

Fills the surface with a solid color, which may be translucent.

**Property Name**: `solidColor`

**Interpolatable**: no

##### agi_rectangularSensor.domeSurfaceMaterial.solidColor.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.domeSurfaceMaterial.image

Fills the surface with an image.

**Property Name**: `image`

**Interpolatable**: no

##### agi_rectangularSensor.domeSurfaceMaterial.image.image

The image to display on the surface.

**Property Name**: `image`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `uri` | Interval | string | The URI value. |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.domeSurfaceMaterial.image.repeat

The number of times the image repeats along each axis.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The numger of times the image repeats along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.domeSurfaceMaterial.grid

Fills the surface with a grid.

**Property Name**: `grid`

**Interpolatable**: no

##### agi_rectangularSensor.domeSurfaceMaterial.grid.color

The color of the surface.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.domeSurfaceMaterial.grid.cellAlpha

Alpha value for the space between grid lines.  This will be combined with the color alpha.

**Property Name**: `cellAlpha`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.domeSurfaceMaterial.grid.lineCount

The number of grid lines along each axis.

**Property Name**: `lineCount`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The number of grid lines along each axis. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.domeSurfaceMaterial.grid.lineThickness

The thickness of grid lines along each axis, in pixels.

**Property Name**: `lineThickness`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The thickness of grid lines along each axis, in pixels. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.domeSurfaceMaterial.grid.lineOffset

The offset of grid lines along each axis, as a percentage from 0 to 1.

**Property Name**: `lineOffset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `cartesian2` | Interval | array | The offset of grid lines along each axis, as a percentage from 0 to 1. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |


#### agi_rectangularSensor.domeSurfaceMaterial.stripe

Fills the surface with alternating colors.

**Property Name**: `stripe`

**Interpolatable**: no

##### agi_rectangularSensor.domeSurfaceMaterial.stripe.orientation

The value indicating if the stripes are horizontal or vertical.

**Property Name**: `orientation`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `StripeOrientation` | Interval | string | The orientation of stripes in the stripe material. Valid values are "HORIZONTAL" or "VERTICAL". |
| `reference` | Interval | string | A reference property. |

##### agi_rectangularSensor.domeSurfaceMaterial.stripe.evenColor

The even color.

**Property Name**: `evenColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.domeSurfaceMaterial.stripe.oddColor

The odd color.

**Property Name**: `oddColor`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.domeSurfaceMaterial.stripe.offset

The value indicating where in the pattern to begin drawing; with 0.0 being the beginning of the even color, 1.0 the beginning of the odd color, 2.0 being the even color again, and any multiple or fractional values being in between.

**Property Name**: `offset`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

##### agi_rectangularSensor.domeSurfaceMaterial.stripe.repeat

The number of time the stripes repeat.

**Property Name**: `repeat`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |



### agi_rectangularSensor.portionToDisplay

Indicates what part of a sensor should be displayed.

**Property Name**: `portionToDisplay`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `portionToDisplay` | Interval | string | Indicates what part of a sensor should be displayed.  Valid values are "COMPLETE", "BELOW_ELLIPSOID_HORIZON", "ABOVE_ELLIPSOID_HORIZON". |
| `reference` | Interval | string | A reference property. |


## agi_vector

Defines a graphical vector that originates at the `position` property and extends in the provided direction for the provided length.

_Note: This type is an extension and may not be implemented by all CZML clients._

**Property Name**: `agi_vector`

**Interpolatable**: no

### agi_vector.show

Whether or not the vector is shown.

**Property Name**: `show`

**Interpolatable**: no

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `boolean` | Interval | boolean | The boolean value. |

### agi_vector.color

The color of the vector.

**Property Name**: `color`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `rgba` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0-255. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `rgbaf` | Interval | array | The color specified as an array of color components [Red, Green, Blue, Alpha] where each component is in the range 0.0-1.0. If the array has four elements, the color is constant. If it has five or more elements, they are time-tagged samples arranged as [Time, Red, Green, Blue, Alpha, Time, Red, Green, Blue, Alpha, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_vector.direction

The direction of the vector.

**Property Name**: `direction`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `axes` | Interval | string | TODO |
| `spherical` | Interval | array | A direction specified as a spherical [Clock, Cone, Magnitude] angles in radians, distance in meters. If the array has three elements, the direction is constant. If it has four or more elements, they are time-tagged samples arranged as [Time, Clock, Cone, Magnitude, Time, Clock, Cone, Magnitude, Time, Clock, Cone, Magnitude, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `unitSpherical` | Interval | array | A direction specified as a unit spherical [Clock, Cone] angles in radians. If the array has two elements, the direction is constant. If it has three or more elements, they are time-tagged samples arranged as [Time, Clock, Cone, Time, Clock, Cone, Time, Clock, Cone, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `cartesian` | Interval | array | The direction represented as a unit Cartesian `[X, Y, Z]`. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where Time is an ISO 8601 date and time string or seconds since `epoch`. |
| `unitCartesian` | Interval | array | The direction represented as a unit Cartesian `[X, Y, Z]`. If the array has three elements, the position is constant. If it has four or more elements, they are time-tagged samples arranged as `[Time, X, Y, Z, Time, X, Y, Z, Time, X, Y, Z, ...]`, where Time is an ISO 8601 date and time string or seconds since `epoch`. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_vector.length

The graphical length of the vector.

**Property Name**: `length`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

### agi_vector.minimumLengthInPixels

The minimum graphical length of the vector in pixels.

**Property Name**: `minimumLengthInPixels`

**Interpolatable**: yes

**Sub-properties**:

| Name | Scope | Type | Description |
|:-----|:------|:-----|:------------|
| `number` | Interval | number or array | The floating-point value. The value may be a single number, in which case the value is constant over the interval, or it may be an array.  If it is an array and the array has one element, the value is constant over the interval. If it has two or more elements, they are time-tagged samples arranged as [Time, Value, Time, Value, ...], where Time is an ISO 8601 date and time string or seconds since epoch. |
| `reference` | Interval | string | A reference property. |
| `epoch` | Packet | string | Specifies the epoch to use for times specifies as seconds since an epoch. |
| `nextTime` | Packet | string or number | The time of the next sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |
| `previousTime` | Packet | string or number | The time of the previous sample within this interval, specified as either an ISO 8601 date and time string or as seconds since epoch. This property is used to determine if there is a gap between samples specified in different packets. |

