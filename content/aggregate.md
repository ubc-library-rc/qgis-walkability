---
layout: default
title: Aggregate
nav_order: 6
parent: Network Analysis
---

## 3. Aggregate

Network analysis
{: .label .label-step}
- Drag and drop GeoJSON files to QGIS canvas
- Extract <b>Centroids</b> from <i>urban_blocks</i> layer
([urban_blocks_centroids.geojson](https://drive.google.com/file/d/1lez2dAiKcUPMF9CvZiHPp1o-XUQ_eAqO/view?usp=sharing))
- Extract <b>Service area (from layer)</b>
  * Vector layer representing the network: <em>street_network</em>
  * Vector layer with start points: <em>block_centroids</em>
  * Travel cost: 300
![600m Buffer Radius](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/map_buffers.png?raw=true)
([urban_blocks_netbuffer.geojson](https://drive.google.com/file/d/1jJ0OuOlyaG5pt2DmSAed82YL6SHL7Mbk/view?usp=sharing))
{: .step}

Join attributes to network buffers (by location)
{: .label .label-step}
- <b>Buffer</b> <i>business</i> layer
  * Radius: 50
  ([retail_business_buffer50.geojson](https://drive.google.com/file/d/1CeCmo7dwpKi51pGhs8xJ8-oaifLSW7wK/view?usp=sharing))
- <b>Join attributes by location</b> from <i>business</i> layer
  * Input layer: <i>network_buffers</i>
  * Join layer: <i>street_intersections</i>
  * Fields: "businesstype"
  * Operations: 'count', 'unique'
- <b>Buffer</b> <i>street_intersections</i> layer
  * Radius: 50
  ([street_intersections_buffer50.geojson](https://drive.google.com/file/d/1dln4bwCM5v7E7AGnnXe8bQZUBwmtD9_n/view?usp=sharing))
- <b>Join attributes by location</b> from <i>street_intersections</i> layer
  * Input layer: <i>network_buffers</i>
  * Join layer: <i>street_intersections</i>
  * Field: "osm_id"
  * Operation: 'count' <br>
- <b>Rename</b> population density column
  * Right-click on <i>census</i> > Properties > Fields > Toggle editing mode
  * Double-click on Population density per square kilometre, 2016 and type pop_den
  * Toggle editing mode and click on Save
- <b>Join attributes by location</b> from <i>census</i> layer
  * Input layer: <i>network_buffers</i>
  * Join layer: <i>census</i>
  * Field: "population density"
  * Operation: 'mean'
  ([urban_blocks_netbuffer_joined.geojson](https://drive.google.com/file/d/1YM7mRALbdlVYJMUmqGpkmoV-2oVuc_6l/view?usp=sharing))

{: .step}

Join attributes from network buffers to urban blocks (by field)
{: .label .label-step}
- Use <b>Join attributes by field value</b> to merge columns to block layer
  * Input layer: <i>urban_blocks</i>
  * Join layer: <i>network_buffers</i>
  * Table field: "fid"
  * Fields: "businesstype_unique", "osm_id_count", "pop_den_mean"
{: .step}

Save joined <i>network_buffers</i> to GeoJSON. Right-click on the layer > Export > Save Features As...
{: .warn}

*1*{: .circle .circle-blue} Use <b>Field calculator</b> to calculate Z-scores (z_intrs, z_pop_den, z_ret_unique, z_ret_count)
  ```
  ("osm_id_count" - mean("osm_id_count")) / stdev("osm_id_count")
  ("pop_den_mean" - mean("pop_den_mean")) / stdev("pop_den_mean")
  ("businesstype_unique" - mean("businesstype_unique")) / stdev("businesstype_unique")
  ("businesstype_count" - mean("businesstype_count")) / stdev("businesstype_count")
  ```
*2*{: .circle .circle-blue} Use <b>Field calculator</b> to sum all normalized indicators
  ```
  (2 * "z_intrs") + "z_pop_den" + "z_ret_unique" + "z_ret_count"
  ```

([urban_blocks_original_joined.geojson](https://drive.google.com/file/d/1PdLcrYYtK4Z5KM_PXybmfEHvdcPVDEHf/view?usp=sharing))
