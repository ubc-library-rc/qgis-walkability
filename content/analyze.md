---
layout: default
title: Analyze
nav_order: 6
parent: Network Analysis
---

<span style="font-size:15px;"> Extract Service Area
</span> 
{: .label .label-step} 
-block centroids here
- Extract **Service area (from layer)**</b>
  * Vector layer representing the network: *street-network*
  * Vector layer with start points: *block-centroids*
  * Path type to calculate: Shortest
  * Travel cost: 300 <!--number dependent-->
- Save output as ***urban-blocks-netbuffer*** <!--(saved as **service-area*** rn for me)-->
    

<span style="font-size:15px;">Buffer network inputs and join attributes
</span> 
- Run a 50m **Buffer** on the pre-processed *businesses* layer. Do **not** dissolve result. 
  * Save Buffered output as ***businesses-buffer50***
- **Join attributes by location (summary)** 
  * Input layer: *urban-blocks-netbuffer*
  * Join layer: *businesses-buffer50*
  * Geometric predicate: Intersect
  * Fields to summarize: "businesstype"
  * Summaries to calculate: 'count', 'unique'
  -
- Run a 50m **Buffer** on the processed layer *street_intersections*. Do **not** dissolve result. 
  * Save Buffered output as ***intersection-buffer50*** 
  ![intersection-buffer](./images/intersection-buffer_20230521.jpg)
- **Join attributes by location (summary)** 
  * Input layer:  *urban-blocks-netbuffer*
  * Join layer: *intersection-buffer50*
  * Geometric predicate: Intersect
  * Fields to summarize: "osm_id"
  * Summaries to calculate: 'count'
  TAKES FOREVER too big an area 
-
- Rename population density column
  * Right-click on *census-DAs* > Properties > Fields > Toggle on editing mode
  * Double-click on Population density per square kilometre, 2016 and type pop_den
  * click Save and toggle editing mode off  
- <b>Join attributes by location</b> from <i>census</i> layer
  * Input layer: *urban-blocks-netbuffer*
  * Join layer: <i>census</i>
  * Field: "population density"
  * Operation: 'mean'


Join attributes from service area to urban blocks (by field)
{: .label .label-step}
- Use <b>Join attributes by field value</b> to merge specific columns 
  * Input layer: <i>urban-blocks</i>
  * Table field: "fid"
  * Input layer 2: *urban-blocks-netbuffer*
  * Table field 2: "fid"
  * Layer 2 fields to copy: "businesstype_unique", "businesstype_count", "osm_id_count", "pop_den_mean"
{: .step}
