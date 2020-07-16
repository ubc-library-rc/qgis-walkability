---
layout: default
title: 3. Analyze
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
- <b>Buffer</b> <i>business</i> layer
  * Radius: 50
- <b>Join attributes by location</b> from <i>business</i> layer
  * Input layer: <i>network_buffers</i>
  * Join layer: <i>street_intersections</i>
  * Fields: "fid" and "businesstype"
  * Operations: 'count', 'unique'
- <b>Buffer</b> <i>street_intersections</i> layer
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
- Save joined <i>network_buffers</i> to GeoJSON
- Use <b>Join attributes by field value</b> to merge columns to block layer
  * Input layer: <i>urban_blocks</i>
  * Join layer: <i>network_buffers</i>
  * Fields: "businesstype_unique", "fid_count", "osm_id_count", "population density_mean"
{: .step}

<br>

*1*{: .circle .circle-blue} Use <b>Field calculator</b> to estimate land use diversity (<i>use_div</i>)
  ```
  "businesstype_unique" / "fid_count"
  ```
*2*{: .circle .circle-blue} Use <b>Field calculator</b> to estimate intersection density (<i>intrs_den</i>)
  ```
  "osm_id_count" / $length
  ```
*3*{: .circle .circle-blue} Use <b>Field calculator</b> to estimate number of retail (<i>ret_count</i>)
  ```
  "fid_count"
  ```
*4*{: .circle .circle-blue} Use <b>Field calculator</b> to calculate Z-scores
  ```
  ("intrs_den" - mean("intrs_den")) / std("intrs_den")
  ("use_div" - mean("use_div")) / std("use_div")
  ("pop_den_mean" - mean("pop_den_mean")) / std("pop_den_mean")
  ("ret_count" - mean("ret_count")) / std("ret_count")
  ```
*5*{: .circle .circle-blue} Use <b>Field calculator</b> to sum all normalized indicators
  ```
  2 * "z_intrs_den" + "z_pop_den_mean" + "z_use_div" + "z_ret_count"
  ```
