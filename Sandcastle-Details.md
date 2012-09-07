New feature ideas for Sandcastle

* Autosave with `localStorage`.
* Warn if closing the tab with unsaved changes.
* Move the highlight code out of `CesiumViewerWidget` into its own thing.  @mramato might tackle this.
* Ability to categorize examples, e.g., like gmail labels.
* Ability for anyone to submit examples to a public gallery like the [GLSL Sandbox](http://glsl.heroku.com/).
* Sandcastle currently uses one template, `bucket.html` to provide the boilerplate
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
