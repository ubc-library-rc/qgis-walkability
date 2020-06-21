---
layout: default
title: 3. Analyze
nav_order: 4
---

- Network analysis
  * Service area from sample centroids
  ![800m Buffer Radius](/images/map_buffers.png)
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

  * Calculate land use diversity
    ```
    "Id_unique" / "Id_sum"
    ```
  * Calculate intersection density
    ```
    "id_count" / $length
    ```
  * Celculate walkability Index
    ```
    2*"intrs_den" + "pop_den_mean" + "use_div" + "Id_count"
    ```
