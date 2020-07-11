---
layout: default
title: 3. Analyze
nav_order: 4
---

Network analysis
{: .label .label-step}
- <b>Service area (from layer)</b>
  * <em>Vector layer representing the network</em>: <b>street_network</b>
  * <em>Vector layer with start points</em>: <b>sample_centroids</b>
  * <em>Travel cost</em>: 800
![800m Buffer Radius](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/map_buffers.png?raw=true)
{: .step}

Spatial join
{: .label .label-step}
- *.*{: .circle .circle-blue} <b>Join attributes by location</b> from <i>intersections</i> layer
  * Field: "id"
  * Operation: 'count'
- *.*{: .circle .circle-blue} <b>Join attributes by location</b> from <i>business</i> layer
  * Fields: "Id" and "businesstype"
  * Operations: 'count', 'unique', 'sum'
- *.*{: .circle .circle-blue} <b>Join attributes by location</b> from <i>dissemination_area</i> layer
  * Field: "population density"
  * Operation: 'mean'
- Save network buffers to gpkg
{: .step}


*1*{: .circle .circle-blue} Use <b>Field calculator</b> to estimate land use diversity (use_div)
  ```
  "businesstype_unique" / "Id_sum"
  ```
*2*{: .circle .circle-blue} Use <b>Field calculator</b> to estimate intersection density (intrs_den)
  ```
  "id_count" / $length
  ```
*3*{: .circle .circle-blue} Use <b>Field calculator</b> to estimate number of retail (ret_count)
  ```
  "businesstype = 'Retail Dealer'
  count("Id")
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
