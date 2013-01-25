**This page is very much a work in progress, contributions are welcome.**

Globe and map applications share many simple tasks in common with each other.  The goal of this page is an attempt to define what those tasks are and describe an architecture that can be used to easily enable applications to perform those tasks with little effort.  To put it more concretely, the goal is to provide Cesium users with a predefined set of actions that can be hooked up to application specific UI.  We also hope to provide a standard HTML toolbar widget for the various web toolkits, such as Dojo and jQuery and make it easy to dynamically build context-sensitive menus.

# Architecture
In order to separate the GUI specific code from the action itself, we propose a new "base" type, `Action` which contains all of the engine-level code to perform a task.

```
TODO: Action prototype pseudo-code
```

# Toolbar Widget

# Table of proposed commands
This table describes some of the actions we have in mind; though there are most likely many more.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
    <th>2D</th>
    <th>3D</th>
    <th>Columbus View</th>
    <th>Mobile</th>
  </tr>
  <tr>
    <th>Stored Views</th>
    <td>Provides a user definable list of standard views.  For example, Earth Fixed, and Earth Inertial reference frames may be here by default and CZML files can specify stored views that showcase a particular event or tour of the data.</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
  </tr>
  <tr>
    <th>Scene Mode</th>
    <td>Allows the user to select between 2D, 3D, and Columbus view modes.</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
  </tr>
  <tr>
    <th>Map Projection</th>
    <td>Allows the user to select between Geographic and Web Mercator projections when in 2D and Columbus view.  Other projections can be added as Cesium supports them.</td>
    <td>Y</td>
    <td>N</td>
    <td>Y</td>
    <td>Y</td>
  </tr>
  <tr>
    <th>Default Mouse</th>
    <td>Puts the user back into the default mouse mode of the current scene mode.</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
    <td>?</td>
  </tr>
  <tr>
    <th>Bounding Box Zoom</th>
    <td>Zooms to a selected bounding box picked on the earth.</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
    <td>?</td>
  </tr>
  <tr>
    <th>Full screen</th>
    <td>Toggles the supplied HTML element (usually the entire Cesium App) into full screen mode.</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
    <td>Y</td>
  </tr>
</table>
