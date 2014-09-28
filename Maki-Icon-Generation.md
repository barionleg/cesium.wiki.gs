Cesium ships with the [Maki icon set](https://github.com/mapbox/maki), which is a set of SVG files created by MapBox for many common map icons. We need to massage them slightly in order to use them effectively.  Thankfully the entire process is automated.  It consists of the following steps.

1. Download and unzip the latest release of the maki icon set.
2. Use [Inkscape](http://www.inkscape.org) on the command line to batch convert the svg files to 512x512 png files.
3. Use a [centerCropResize](https://github.com/mramato/centerCropResize) to crop/center/resize the PNG files so they can be used by Cesium.
4. Use [pngCrush](http://pmt.sourceforge.net/pngcrush/)
5. Replace the Cesium `Source/Assets/Textures/maki` directory with the new icons.

The below bash script can be run inside of the src directory of the maki release.  All you have to do is take the generated png files and move them to Cesium.

```
#!/bin/bash
for svgFile in *-24.svg; do
  pngFile="${svgFile%-24.svg}.png"
  crushedFile="${pngFile%.png}-crushed.png"
  inkscape "$svgFile" --export-png=$pngFile -w 512 -h 512
  centerCropResize $pngFile 96
  pngcrush $pngFile $crushedFile
  mv $crushedFile $pngFile;
done
```