**This is now out-of-date.  There will be a new version as part of [#1683](https://github.com/AnalyticalGraphicsInc/cesium/issues/1683).**

## Units

* Use meters for distances.
* Use radians, not degrees, for angles.
* Use seconds for time durations.

## Constructors

* Constructor functions should take the objects's basic components as parameters, while static helper methods should be provided for constructing an object via other means.  Helper methods should be prefixed with "from":

```javascript
var julianDate = new JulianDate(dayNumber, secondsOfDay, TimeStandard.UTC);
var julianDateFromIso8601 = JulianDate.fromIso8601("2012-04-24T18:08Z");
var julianDateFromDate = JulianDate.fromDate(new Date(1980, 7, 1));
```

* Object methods which create a new instance of a different object should be prefixed with "to":

```javascript
var julianDate = new JulianDate(dayNumber, secondsOfDay, TimeStandard.UTC);
var javaScriptDate = julianDate.toDate();
```

## Making a copy of `this`

If a closure needs a copy of `this`, our convention is to name it `that`.

```javascript
var that = this;
```

Some projects use the name `self` instead of `that` here.  However, `self` is already defined by the browser as a reference to the current window, and we wish to avoid redefining built-in variables.

## `null` vs. `undefined`

Where possible, avoid use of `null` and prefer `undefined`.  To test for this condition, use:

```javascript
if (typeof myVariable === 'undefined') {
    // take action
}
```

or

```javascript
if (typeof myVariable !== 'undefined') {
    // take action
}
```

The problem with comparing `myVariable === undefined` directly is that the variable `undefined` itself
is capable of being re-defined in JavaScript, so the JIT compiler can't make assumptions about what the
meaning of `undefined` will actually be at runtime.  In the recommended comparison, `typeof` is a language keyword, and
`'undefined'` in single quotes is a string literal that can't change at runtime, so the only variable is
`myVariable` itself.  Armed with this, the JIT can avoid string comparisons and optimize the entire statement
into a single machine-language null pointer check (or similar).  Thus, although it looks like asking for a string
comparison, this statement executes faster than a direct comparison with the variable `undefined`.

## Functions

* If a sensible default exists for a function argument or object property, don't require the user to provide it.  Examples:
   * ellipsoid - `Ellipsoid.getWgs84()`
   * granularity - `CesiumMath.toRadians(1.0)`
   * height - `0.0`
* Likewise if a function argument is required, throw a `DeveloperError` if it is not provided, not in range, etc.
* Public functions should treat Cartesian and Quaternion type arguments as if they are immutable, and also accept the equivalent object literal.  For example these two lines of code have the same effect:

```javascript
foo(new Cartesian3(1.0, 2.0, 3.0));
foo({ x : 1.0, y : 2.0, z : 3.0 });
```

* Public functions should always return a Cartesian or Quaternion type, not an equivalent object literal.  For example:

```javascript
var v = bar();     // Returns a Cartesian3
v = v.normalize(); // Works because it is a Cartesian3, not an object with just x, y, and z properties
```

## Variables

* To aid the human reader, append `.0` to whole numbers intended to be floating-point values, e.g., `var f = 1.0;`.

## Formatting

In general, format new code the same as the existing code.

* Use four (4) spaces for indentation.  Do not use [tab characters](http://www.jwz.org/doc/tabs-vs-spaces.html).
* Use single quotes, `'`, instead of double quotes, `"`.  `"use strict"` is an exception and should use double quotes.
* Where possible, eliminate all `jsHint` warnings.  The [[Contributor's Guide]] explains how to set up Eclipse to display these warnings.
