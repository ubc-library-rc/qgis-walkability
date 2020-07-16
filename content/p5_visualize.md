---
layout: default
title: 5. Visualize
nav_order: 6
---

Visualize results
{: .label .label-step}
- Display walkability index using graduated scheme
  * Right-click on the layer > Properties > Symbology
  * From the upper bar, select Graduated
  * Chose the value and click Classify > Apply
- Try different color ramps and classification modes
{: .step}

Custom basemap
{: .label .label-step}
- In the browser, right-click on XYZ Tiles > New Connection...
  * Name: ESRI Satellite
  * URL:
```
  https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}
```
- Change basemap to black and white
  * Right-click on <i>ESRI Satellite</i> > Properties > Symbology > Grayscale > By lightness
- Try layer overlay effect
  * Right-click on <i>urban_blocks</i> > Properties > Symbology > Layer rendering > Layer > Overlay
{: .step}
