## New "Playback" widget

(This is part of the [Widget roadmap](Widget-Details).)

As of this writing, the master branch `CesiumViewerWidget` has a toolbar that looks like this:

<p align="center"><img src="wiki/screenshots/playback-widget/OldToolbar.png" alt="Old toolbar" /></p>

The proposed replacement `Playback` widget pops up looking like this:

<p align="center"><img src="wiki/screenshots/playback-widget/Playback1.png" alt="Playback widget" /></p>

The bottom-left is "Reset" (same as before).  On the right is faster/slower, same as before.  The large
middle button acts as a play/pause toggle, or really a pause/un-pause toggle where "un-pause" puts you
back into whatever mode you might have been in before pause (rewind, realtime, etc).

The upper-left button is called "Shuttle ring."  Clicking it results in this:

<p align="center"><img src="wiki/screenshots/playback-widget/Playback2.png" alt="Shuttle ring" /></p>

The shuttle ring is may look familiar to folks who have used video editing systems.  It is a ring
offering a continuous control of forward and backward speeds.  You can slide the "green glow" indicator
smoothly around its entire edge, like this:

<p align="center"><img src="wiki/screenshots/playback-widget/ManyPlayback_1row.png" alt="Various modes" /></p>

There is also a button tucked under the top-center of the ring, called the realtime button.  It sets the
time to "now" (from the computer's own clock) and animates along at real time.  Pausing this mode for a
length of time, and then un-pausing via the center button, will cause it to jump forward to catch up with
realtime.  Using the shuttle ring will pop out of realtime as you expect, and animate forwards or
backwards from there.

This functionality is available for testing now on the `playback` branch.  It's implemented in
SVG and works on mobile (FF & Chrome for Android), although currently you can only tap, not slide the
shuttle ring on mobile (touch events not hooked up yet, pending resolution of the `camera` and `pinch-zoom`
branches).  In the meantime you can test it as a work-in-progress on mobile, and more fully test
it on a desktop/laptop.

One remaining needed feature is the ability to apply themes.  After some discussion, the proposed plan
involves adding a CSS style sheet, reading values from that sheet in JS, and constructing the SVG
gradients based on the values read.  This would allow simple CSS styling of something that otherwise
would require changes to SVG-generating JS code.  Again, feedback welcome, particularly from third
parties who are trying to integrate Cesium with other systems.
