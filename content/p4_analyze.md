---
layout: default
title: 3. Analyze
nav_order: 4
---

- Network analysis
  * Service area from sample centroids
  ![800m Buffer Radius](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/map_buffers.png?raw=true)
  * Join attributes from intersections layer
    * id
    * count
  * Join attributes from business layer
    * Id, businesstype
    * count, unique, sum
  * Join attributes from census DA layer
    * population density
    * mean
  * Save network buffer to gpkg
***
- Calculate indicators

  * Calculate land use diversity (use_div)
    ```
    "businesstype_unique" / "Id_sum"
    ```
  * Calculate intersection density (intrs_den)
    ```
    "id_count" / $length
    ```
  * Calculate number of retail (ret_count)
    ```

    ```
  * Calculate Z-scores
    ```
    ("intrs_den" - mean("intrs_den")) / std("intrs_den")
    ("use_div" - mean("use_div")) / std("use_div")
    ("pop_den_mean" - mean("pop_den_mean")) / std("pop_den_mean")
    ("ret_count" - mean("ret_count")) / std("ret_count")
    ```
  * Calculate walkability Index
    ```
    2*"z_intrs_den" + "z_pop_den_mean" + "z_use_div" + "z_ret_count"
    ```
