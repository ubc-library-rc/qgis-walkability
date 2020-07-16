---
layout: default
title: 4. Calculate
nav_order: 5
---

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
