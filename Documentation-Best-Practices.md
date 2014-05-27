Cesium uses [JSDoc3](http://usejsdoc.org/index.html) for reference documentation, which is generated as part of a release build.  Here are the best practices we use.

## Reference

* Use `@see` to link to related classes, functions, and online resources.
* Use `<code> </code>` tags when referring to parameters or other variable names and values within a description.
* Use `{@link className}` to link to another documented type.  This is not required for `@param` tags when the type is provided.

## Examples

* Provide an `@example` for all non-trivial functions and properties.  Users will look for an example before reading the actual doc.
* Limit code in `@example` tags to 80 lines so it does not overflow.

## Classes

* Prefer `@alias` over `@name` for documenting classes and modules. `@name` will treat the documentation comment in isolation, ignoring surrounding comments, such as those for public properties. 
* Use the `@memberof` tag to document class functions.
* Constructors defined within an anonymous function that returns a module should have the following structure:

```javascript
/**
 * ...
 * @constructor
 */
 var foo = function() {
    ...
 };
```

* Use `@exports moduleName` to document modules, including static classes and standalone functions.

## Parameters
* Use square brackets to indicate an optional parameter.

```javascript
/**
 * @param {String} [foo] Description of foo.
 */
```

* Provide default values for parameters within square brackets.

```javascript
/**
 * @param {String} [foo='bar'] Description of foo.
 */
```
  
* When a function expects a template object literal as an argument, document each expected property individually: 

```javascript
/**
 * ...
 * @param {Object} options An object containing parameters.
 * @param {Number} options.x The tile x coordinate.
 * @param {Number} options.y The tile y coordinate.
 * @param {Number} options.zoom The tile zoom level.
 * @param {Tile} description.parent The parent of this tile in a tile tree system.
 * ...
 */
var Tile = function(description) {
   ...
};
```

## General Layout
There's a general flow to each documentation block that makes it easy to read. Tags are always in the same order with the same spacing.

```
Description
@ memberOf or alias or exports Name
blank line
@ params
@ returns
blank line
@ exceptions
blank line
@ examples (formatted just like the rest of the code. and useful comments if it's only boilerplate)
blank line
@ see
```

## Detailed Example
The following is an example of how to fully document a class, including properties and methods. For the complete code, see [Cartesian2](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/Source/Core/Cartesian2.js).

```javascript
define(function() {
    "use strict";

    /**
     * A 2D Cartesian point.
     *
     * If either <code>x</code> or <code>y</code> is undefined, then the corresponding
     * component will be initialized to 0.0.
     *
     * @alias Cartesian2
     * @constructor
     *
     * @param {Number} x The x-coordinate for the Cartesian type.
     * @param {Number} y The y-coordinate for the Cartesian type.
     *
     * @see Cartesian3
     * @see Cartesian4
     */
    var Cartesian2 = function(x, y) {

        /**
         * The Cartesian's x-coordinate.
         *
         * @type Number
         *
         * @see Cartesian2.y
         */
        this.x = (typeof x !== 'undefined') ? x : 0.0;

        /**
         * The Cartesian's y-coordinate.
         *
         * @type Number
         *
         * @see Cartesian2.x
         */
        this.y = (typeof y !== 'undefined') ? y : 0.0;
    };

    /**
     * Returns true if this Cartesian equals <code>other</code> componentwise.
     *
     * @memberof Cartesian2
     * @param {Cartesian2} other The Cartesian to compare for equality.
     * @return {Boolean} <code>true</code> if the Cartesians are equal componentwise; otherwise, <code>false</code>.
     * 
     * @example
     * var v = new Cartesian2(1, 2);
     * var w = new Cartesian2(1, 2);
     * var result = v.equals(w);    // true
     */
    Cartesian2.prototype.equals = function(other) {
        return (this.x === other.x) && (this.y === other.y);
    };

    return Cartesian2;
});
```