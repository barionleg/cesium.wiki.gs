## New feature ideas for Sandcastle

* Autosave with `localStorage`.
* Warn if closing the tab with unsaved changes.
* Move the highlight code out of `CesiumViewerWidget` into its own thing.  @mramato might tackle this.
* Ability to categorize examples, e.g., like gmail labels.
* Ability for anyone to submit examples to a public gallery like the [GLSL Sandbox](http://glsl.heroku.com/).
* Control sort order of gallery?
* If the Run button is yellow, maybe the primitive hover code highlight thing should stop.
* Hook up Sandcastle declare/highlight functions to auto-complete.
* If Cesium throws errors that it can't load imagery, show those errors in Sandcastle console.

## Supporting GLSL and CZML editing

We want Sandcastle to be able to live-edit [CZML files](CZML-Guide), as well as vertex and
fragment shaders for GLSL materials.  Certainly more instances of CodeMirror can be added
to the tabbed window on the left, and we might also require that the files share the same
base filename with the HTML, like the JPG thumbnail does.  The tricky part is, we "save"
(download) from Sandcastle to a single HTML file, and if we roll GLSL and CZML into that
file, then they no longer have their own separate extensions, limiting their usefulness
outside of Sandcastle.  Perhaps this could be solved with import and export buttons on
the code editors themselves, or import/export buttons in the "Save As" drop down.

Note that including CZML files in the HTML save itself might greatly increase the amount
of memory needed, particularly for searching the gallery.  Perhaps these should always
be separate, with their own import/export.  In fact, maybe stand-alone CZML files with
JPG thumbnails could exist in the gallery with no custom code to go with them.  Does
that limit options to prototype custom code alongside custom CZML?  Could we do both?

It would also be nice to be able to import and export CZML materials for use in other
projects, and maybe whole 3D models too.
