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


* Use `@exports moduleName` to document modules that are not classes, including standalone functions.

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
