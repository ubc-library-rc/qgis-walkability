---
layout: default
title: 3. Analyze
nav_order: 4
---

- Network analysis
  * Service area from sample centroids
  * Join attributes from intersections layer
    * id
    * count
  * Join attributes from business layer
    * Id, businesstype
    * count, unique
  * Join attributes from census DA layer
      * population density
      * mean
  * Save network buffer to gpkg
- Calculate index
  * Calculate intersection density
  `"id_count" / $length`

  * Field calculator (2*"intrs_den" + "pop_den_mean" + )
