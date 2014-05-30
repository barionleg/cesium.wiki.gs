Cesium uses [JSDoc3](http://usejsdoc.org/index.html) for reference documentation, which is generated as part of a release build.  Here are the best practices we use.

## Reference

* Use `@see` to link to related classes, functions, and online resources.
* Use `<code> </code>` tags when referring to parameters or other variable names and values within a description.
* Use `{@link className}` to link to another documented type.  This is not required for `@param` tags when the type is provided.
* Use `{@link URL|title}` to link to external sites.

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
 * @param {Tile} options.parent The parent of this tile in a tile tree system.
 * ...
 */
var Tile = function(description) {
   ...
};
```

## General Layout
There's a general flow to each documentation block that makes it easy to read. Tags are always in the same order with the same spacing.

```
Description.

@memberOf|alias|exports Name
@constructor

@param {Type} name Description.
@param {Type|OtherType} name Description with long
       wrapping lines.
@returns {Type} Description.

@exception {Type} Description.

@see Type
@see Type#instanceMember
@see Type.staticMember

@example 
(formatted just like the rest of the code. and useful comments if it's only boilerplate)
```

## Detailed Example
The following is an example of how to fully document a class, including properties and methods. For the complete code, see [Cartesian2](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/Source/Core/Cartesian2.js).

```javascript
    /**
     * A 2D Cartesian point.
     *
     * @alias Cartesian2
     * @constructor
     *
     * @param {Number} [x=0.0] The X component.
     * @param {Number} [y=0.0] The Y component.
     *
     * @see Packable
     * @see Cartesian3
     * @see Cartesian4
     */
    var Cartesian2 = function(x, y) {
        /**
         * The Y component.
         * 
         * @type {Number}
         * @default 0.0
         */
        this.x = defaultValue(x, 0.0);

        /**
         * The X component.
         * 
         * @type {Number}
         * @default 0.0
         */
        this.y = defaultValue(y, 0.0);
    };

    /**
     * Compares the provided Cartesians componentwise and returns
     * <code>true</code> if they are equal, <code>false</code> otherwise.
     * 
     * @memberof Cartesian2
     *
     * @param {Cartesian2} [left] The first Cartesian.
     * @param {Cartesian2} [right] The second Cartesian.
     * @returns {Boolean} <code>true</code> if left and right are equal, <code>false</code> otherwise.
     */
    Cartesian2.equals = function(left, right) {
        return (left === right) ||
               ((defined(left)) &&
                (defined(right)) &&
                (left.x === right.x) &&
                (left.y === right.y));
    };
```