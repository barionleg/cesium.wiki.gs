Cesium uses [JSDoc3](http://usejsdoc.org/index.html) for reference documentation, which is generated as part of a release build.  Here are the best practices we use.

## Reference

* Provide an `@example` for all non-trivial functions and properties.  Users will look for an example before reading the actual doc.
* Use `@see` to link to related classes, functions, and online resources.
* Use `<code> </code>` tags when referring to parameters or other variable names and values within a description.
* Use `{@link className}` to link to another documented type.  This is not required for `@param` tags when the type is provided.

## Classes

* Prefer `@alias` over `@name` for documenting classes and modules. `@name` will treat the documentation comment in isolation, ignoring surrounding comments, such as those for public properties. 
* Use the `@memberof` tag to document class functions.
* Constructors defined within an anonymous function that returns a module should have the following structure:

<pre>
/**
 * ...
 * @constructor
 */
 var foo = function() {
    ...
 };
</pre>


* Use `@exports moduleName` to document modules, including static classes and standalone functions.

## Parameters
* Use square brackets to indicate an optional parameter.

<pre>
/**
 * @param {String} [foo] Description of foo.
 */
</pre>

* Provide default values for parameters within square brackets.

<pre>
/**
 * @param {String} [foo="bar"] Description of foo.
 */
</pre>
  
* When a function expects a template object literal as an argument, document each expected property individually: 

<pre>
/**
 * ...
 * @param {Number} description.x The tile x coordinate.
 * @param {Number} description.y The tile y coordinate.
 * @param {Number} description.zoom The tile zoom level.
 * @param {Tile} description.parent The parent of this tile in a tile tree system.
 * ...
 */
var Tile = function(description) {
   ...
};
</pre>

## Detailed Example
The following is an example of how to fully document a class, including properties and methods. For the complete code, see [Cartesian2](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/Source/Core/Cartesian2.js).

<pre>
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
         * DOC_TBA
         *
         * @type Number
         *
         * @see Cartesian2.y
         */
        this.x = (typeof x !== 'undefined') ? x : 0.0;

        /**
         * DOC_TBA
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
     */
    Cartesian2.prototype.equals = function(other) {
        return (this.x === other.x) && (this.y === other.y);
    };

    return Cartesian2;
});


</pre>