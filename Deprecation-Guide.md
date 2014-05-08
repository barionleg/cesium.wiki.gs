We strive to keep the Cesium API stable but also maintain mobility for speedy development and to take the API in the right direction.

A `@private` API is considered a Cesium implementation detail and can be broken immediately without deprecation.

A public API (class, function, property) should be deprecated before being removed.  To do so:

1. Decide on which future version the deprecated API should be removed.  This is on a case-by-case basis depending on how badly it impacts users and Cesium development.  Most deprecated APIs will removed in 1-3 releases.  This can be discussed in the pull request if needed.
1. Use `deprecationWarning` to warn users that the API is deprecated and what proactive changes they can take.
1. Add the [`@deprecated`](http://usejsdoc.org/tags-deprecated.html) doc tag.
1. Add it to the `Deprecated` section of [`CHANGES.md`](https://github.com/AnalyticalGraphicsInc/cesium/blob/master/CHANGES.md) and in what version it will be removed.
1. Create an [issue](https://github.com/AnalyticalGraphicsInc/cesium/issues) to remove the API with the appropriate `remove in [version]` label.