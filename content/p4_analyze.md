---
layout: default
title: 3. Aggregate
nav_order: 4
---

Network analysis
{: .label .label-step}
- Drag and drop GeoJSON files to QGIS canvas
- Extract <b>Centroids</b> from <i>urban_blocks</i> layer
- Extract <b>Service area (from layer)</b>
  * Vector layer representing the network: <em>street_network</em>
  * Vector layer with start points: <em>block_centroids</em>
  * Travel cost: 600
![600m Buffer Radius](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/map_buffers.png?raw=true)
{: .step}

Spatial join
{: .label .label-step}
<br><b>Buffer</b> <i>business</i> layer
  * Radius: 50
<br><b>Join attributes by location</b> from <i>business</i> layer
  * Input layer: <i>network_buffers</i>
  * Join layer: <i>street_intersections</i>
  * Fields: "fid" and "businesstype"
  * Operations: 'count', 'unique'
<br><b>Buffer</b> <i>street_intersections</i> layer
  * Radius: 50
- <b>Join attributes by location</b> from <i>street_intersections</i> layer
  * Input layer: <i>network_buffers</i>
  * Join layer: <i>street_intersections</i>
  * Field: "osm_id"
  * Operation: 'count' <br>
- <b>Join attributes by location</b> from <i>census</i> layer
  * Input layer: <i>network_buffers</i>
  * Join layer: <i>census</i>
  * Field: "population density"
  * Operation: 'mean'
- Use <b>Join attributes by field value</b> to merge columns to block layer
  * Input layer: <i>urban_blocks</i>
  * Join layer: <i>network_buffers</i>
  * Fields: "businesstype_unique", "fid_count", "osm_id_count", "population density_mean"
{: .step}

Save joined <i>network_buffers</i> to GeoJSON
  * Right-click on the layer > Export > Save Features As...
{: .warn}
