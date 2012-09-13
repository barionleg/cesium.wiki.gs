## New feature ideas for Sandcastle

* Autosave with `localStorage`.
* Warn if closing the tab with unsaved changes.
* Move the highlight code out of `CesiumViewerWidget` into its own thing.  @mramato might tackle this.
* Ability to categorize examples, e.g., like gmail labels.
* Ability for anyone to submit examples to a public gallery like the [GLSL Sandbox](http://glsl.heroku.com/).
* Add textbox to edit gallery metadata.
* Control sort order of gallery?
* Replace deprecated `BlobBuilder` with actual `Blob` constructor (once that constructor is in stable FF & Chrome, see comments in Sandcastle source).
* If Cesium throws errors that it can't load imagery, show those errors in Sandcastle console.
* Certain kinds of errors (such as calling `foo();`) don't provide line numbers, can this be fixed?
   * Dojo is intercepting these errors with code like the following, maybe it can be overridden.
<pre>
if (!error || error.log !== false) {
    (dojo.config.deferredOnError || function(x){ console.error(x); })(error);
}
</pre>

## Supporting non-Dojo, GLSL, CZML editing

Sandcastle currently uses one template, `bucket.html` to provide the boilerplate
code that gets baked into every Sandcastle gallery entry.  The current code here does not
include Cesium itself, but does include Dojo (for technical reasons, Dojo support would not
be possible in Sandcastle without this dependency).  We should allow Sandcastle to operate
in different "modes" that use different `bucket.html` templates with different editable
sections.  The various templates would include:
   * A Dojo-enabled bucket, the same as we have now
   * A Dojo-free bucket for using Cesium without any Dojo references
   * A Cesium material editor including GLSL editor windows
   * A CZML file editor, possibly with a customizable Viewer
   * A 3D model editor when that's available
