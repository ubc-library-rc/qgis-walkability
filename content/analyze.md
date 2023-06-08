---
layout: default
title: Analyze
nav_order: 6
parent: Network Analysis
---

<span style="font-size:15px;"> Extract Service Area
</span> 
{: .label .label-step} 
- Extract **Service area (from layer)**</b>
  * Vector layer representing network: *street-network*
  * Path type to calculate: Shortest
  * Vector layer with start points: *block-centroids*
  * Travel cost: 300 
* Save output as ***street-network-buffer*** 
<!--issue is that fid isnt saved and subsequent joins output each join layer and dont join atts to initial table-->
{: .step}

<span style="font-size:15px;"> Buffer network inputs and join attributes
</span>
{: .label .label-step} 
- Run a 50m **Buffer** on the pre-processed *businesses* layer. Do **not** dissolve result. 
- **Join attributes by location (summary)** 
  * Input layer: *street-network-buffer*
  * Join layer: Buffered layer
  * Geometric predicate: intersects
  * Fields to summarize: "businesstype"
  * Summaries to calculate: 'count', 'unique'
- Run a 50m **Buffer** on the processed layer *street_intersections*. Do **not** dissolve result. 
- **Join attributes by location (summary)** 
  * Input layer:  *street-network-buffer*
  * Join layer: Buffered layer
  * Geometric predicate: intersects
  * Fields to summarize: "osm_id"
  * Summaries to calculate: 'count'      
- **Join attributes by location (summary)** 
  * Input layer: *street-network-buffer*
  * Join layer: *census*
  * Fields to summarize: "pop_den"
  * Summaries to calculate: 'mean'
- You will now have 3 temporary output files called Join layer with the summary calculations. 
{: .step}

do three join attributes by field to join 

<span style="font-size:15px;"> Join attributes from service area to urban blocks (by field)
</span> 
{: .label .label-step}
- Use <b>Join attributes by field value</b> to merge specific columns 
  * Input layer: <i>urban-blocks</i>
  * Table field: geo_point_2d
  * Input layer 2: *Joined Layer*
  * Table field 2: geo_point_2d
  * Layer 2 fields to copy: "businesstype_unique", "businesstype_count", "osm_id_count", "pop_den_mean"
{: .step}

clip to census ? 

<span style="font-size:15px;"> Use <b>Field calculator</b> to calculate Z-scores 
</span> 
{: .label .label-step}
- Open attribute table of *index* and toggle on editing mode
- Create four new fields by pasting the following calculations into **Field calculator**. For each, change **Output field type** to **Decimal number (real)** and keep precision at 3 places. 
  ```
  z_intrs = ("osm_id_count" - mean("osm_id_count")) / stdev("osm_id_count")
  z_pop_den = ("pop_den_mean" - mean("pop_den_mean")) / stdev("pop_den_mean")
  z_ret_unique = ("businesstype_unique" - mean("businesstype_unique")) / stdev("businesstype_unique")
  z_ret_count = ("businesstype_count" - mean("businesstype_count")) / stdev("businesstype_count")
  ```
<img src="./images/field-calculator_20230608.jpg" style="width:60%">
- Create one last field called *walkability* and use <b>Field calculator</b> to sum all normalized indicators
  ```
  (2 * "z_intrs") + "z_pop_den" + "z_ret_unique" + "z_ret_count"
  ```
- Save changes and toggle off editing mode
{: .step}