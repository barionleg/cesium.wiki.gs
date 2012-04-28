In progress...

## Units

* Use meters for distances.
* Use radians, not degrees, for angles.

## Constructors
* Constructor functions should take the objects's basic components as parameters, while static helper methods should be provided for constructing an object via other means.  Helper methods should be prefixed with "from":

<pre>
var julianDate = new JulianDate(dayNumber, secondsOfDay, TimeStandard.UTC);
var julianDateFromIso8601 = JulianDate.fromIso8601("2012-04-24T18:08Z");
var julianDateFromDate = JulianDate.fromDate(new Date(1980, 7, 1));
</pre>

* Object methods which create a new instance of a different object should be prefixed with "to":

<pre>
var julianDate = new JulianDate(dayNumber, secondsOfDay, TimeStandard.UTC);
var javaScriptDate = julianDate.toDate();
</pre>

## Functions

* If a sensible default exists for a function argument or object property, don't require the user to provide it.  Examples:
   * ellipsoid - `Ellipsoid.getWgs84()`
   * granularity - `CesiumMath.toRadians(1.0)`
   * height - `0.0`
* Likewise if a function argument is required, throw a `DeveloperError` if it is not provided, not in range, etc.
* Public functions should treat Cartesian and Quaternion type arguments as if they are immutable, and also accept the equivalent object literal.  For example these two lines of code have the same affect:

<pre>
foo(new Cartesian3(1.0, 2.0, 3.0));
foo({ x : 1.0, y : 2.0, z : 3.0 });
</pre>

* Public functions should always return a Cartesian or Quaternion type, not an equivalent object literal.  For example:

<pre>
var v = bar();     // Returns a Cartesian3
v = v.normalize(); // Works because it is a Cartesian3, not an object with just x, y, and z properties
</pre>

## Testing

* It is important to have excellent test coverage since JavaScript doesn't have the safety net of a compiler and linker.
* Prefer fine-grained tests over coarse-grained tests because they are easier to debug. In particular, only have one `expect().toThrow()` per spec.
* When testing for exceptions, only wrap the function call that will throw the exception. For example, prefer:

<pre>
var va = Context.createVertexArray();
va.destroy();
expect(function () { va.destroy(); }).toThrow();
</pre>
over:

<pre>
expect(function () { var va = Context.createVertexArray(); va.destroy(); va.destroy(); }).toThrow();`
</pre>
Otherwise, an unexpected exception can go unnoticed.

## Formatting

* Use four spaces for tabs