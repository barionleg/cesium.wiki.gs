## Widget improvements

There are efforts underway to improve widget architecture and reduce dependence on third party libraries
like Dojo.  Much of this is still under debate and feedback is most welcome.

## New architecture

An effort is underway on the `simple-widget` branch to extract all non-Dojo code from the `CesiumViewerWidget`
and create a new `Source/Widgets/Viewer.js` that gets bundled into the combined `Cesium.js` file and
is immediately usable in sample programs.  For example, the basic sample program on the `simple-widget` branch
looks like this:

```
<html><head>
    <title>Cesium Demo</title>
    <script type="text/javascript" src="../Build/Cesium.js"></script>
	<style> /* .fullSize {...} */ </style>
</head>
<body>
    <div id="cesiumContainer" class="fullSize"></div>
    <script>

        var parentNode = document.getElementById('cesiumContainer');

        var widget = new Cesium.Viewer(parentNode, {
            imageBase : '../Source/Assets/Imagery/'
        });

    </script>
</body>
</html>
```

The `imageBase` option is a temporary measure.  The plan is to design some kind of global `Assets` locator,
such as using the `CESIUM_BASE_URL` global (already used by Cesium workers), or implementing a
`data-base-url` attribute on the `script` tag itself, similar to how Dojo finds its resources.  This type
of asset locator would reduce the script code to this:

```javascript
    var parentNode = document.getElementById('cesiumContainer');
    var widget = new Cesium.Viewer(parentNode);
```

As things stand now (2012-11-28), the widget above is almost a line-for-line copy of `CesiumViewerWidget`
in master, with the Dojo UI removed but all of the CZML processing intact.  The two are still fairly easy to
diff, so that as new features are added to `CesiumViewerWidget` they can be directly copied to `Cesium.Viewer`.
Here is an example of CZML being loaded into the new widget:

```javascript
    var parentNode = document.getElementById('cesiumContainer');

    var endUserOptions = {
        'source' : '../../CesiumViewer/Gallery/LotsOfSensors.czml'
    };

    var viewer = new Cesium.Viewer(parentNode, {
        imageBase : '../../../Source/Assets/Imagery/',  // Remove this line with new Assets system.
        endUserOptions : endUserOptions,
        enableDragDrop : true
    });
```

There is ongoing debate as to how best to add UI to such a system.  Custom UI can easily be added with any
third-party widget set, such as Dojo or jQueryUI.  But could there be any UI that gets
rolled into `Cesium.js` for everyone to use?  I propose at least two UI elements:

* The Timeline widget is not typical UI toolkit material, has no dependency on other UI libraries, and is useful for scrubbing through `JulianDate` time in Cesium.  The visual theme can be controlled by adding a custom CSS stylesheet.

* The [Playback widget](Playback-Details) works with the timeline widget, also has no dependency on other libraries, and is also not a typical UI toolkit kind of widget.

It's easy to bundle the the above two with `Cesium.js`, and integrate with UI elements from other
toolkits.  But the `CesiumViewerWidget` offers a bit more UI that is harder to classify:

* A full-screen button
* A 3D/2D/Columbus View mode selector
* An imagery selector
* A Home view button, possibly could turn into a set of stored views.

These are more traditional UI elements, and there is an argument to be made that they should be kept out
of Cesium proper and only added with third-party widget toolkits.  The "business logic" can exist in
the core widget, connected by events or callbacks to a third-party toolkit.  The downside of this
obvious path is that they will need to be re-connected for each new toolkit we hope to support: There
will be some level of effort to make any new toolkit display the right buttons and pull-downs, hook
up the events, and share a CSS theme with the other Cesium widgets.  Also, taking this approach means
that our simplest demos, like the one above, would display only the timeline and playback widgets,
without any UI to change to Columbus View mode or reset to the home view.

Among the Cesium devs there is a strong desire to avoid designing our own widget toolkit.  We don't
want to replicate any work that has already been done by Dojo, jQueryUI, and the others.  But the
bulk of the UI we need is either extremely customized (timeline & playback), or simple push-button
(3D/2D, fullscreen, etc), the latter of which is trivial to implement with [vanilla JS](http://vanilla-js.com/).  

The sticking point is the more complex widgety stuff, namely the imagery selector and the stored
view picker, and any future elements we decide to make available as part of Cesium itself.  Implementing
these is straightforward, but places us at risk of duplicating some effort of real widget toolkits,
which we wish to avoid.  It may be that these functions should be left off of the commonly available
UI elements, and we have separate implementations for jQueryUI, Dojo, and other toolkits.

Ideas and feedback on all of the above is welcome on our [mailing list](https://groups.google.com/forum/?fromgroups=#!forum/cesium-dev).

## New "Playback" widget

Read more about the proposed [Playback widget](Playback-Details).

<p align="center"><a href="Playback-Details"><img src="wiki/screenshots/playback-widget/Playback2.png" alt="Shuttle ring" /></a></p>
