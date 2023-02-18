---
layout: default
title: Visualize Index
nav_order: 5
---

Visualize results
{: .label .label-step}
- Display walkability index using graduated scheme
  * Right-click on the layer select <b>Properties</b> > <b>Symbology</b>
  * From the upper bar, select <b>Graduated</b>
  * Chose the value and click <b>Classify</b> > <b>Apply</b>
- Try different color ramps and classification modes
{: .step}

Custom basemap
{: .label .label-step}
- In the browser, right-click on <b>XYZ Tiles</b> > <b>New Connection...</b>
  * Name: ESRI Satellite
  * URL:
```
  https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}
```
- Change basemap to black and white
  * Right-click on <i>ESRI Satellite</i> > <b>Properties</b> > <b>Symbology</b> > <b>Grayscale</b> > <b>By lightness</b>
- Try layer overlay effect
  * Right-click on <i>urban_blocks</i> > <b>Properties</b> > <b>Symbology</b> > <b>Layer rendering</b> > <b>Layer</b> > <b>Overlay</b>
![Walkability Index](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/walkability_final.png?raw=true)
{: .step}
