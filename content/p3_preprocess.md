---
layout: default
title: 2. Preprocess
nav_order: 3
---

- Pre process samples
  * Reproject boundaries
  * Reproject samples
  * Extract samples within boundaries
  * Get centroids of samples
  * Buffer and dissolve centroids (800m)
  * Save Blocks, Centroids and Boundary to GeoPackage
  ![Preprocess samples]()
- Pre process street network
  * Reproject line geometry
  * Fix street line geometries
  * Extract line intersections
  * Buffer and dissolve intersections
  * Convert to single-parts
  * Find centroids of buffers
  * Buffer intersection to create a polygon
  * Extract intersections within boundary
  * Save Intersections to GeoPackage
  ![Preprocess streets]()
- Pre process dissemination area
  * Open census DA
  * Fix census polygon geometries
  * Extract DAs within boundary
  * Save Census to GeoPackage
- Pre process business licenses
  * Filter valid licenses by expression
  ```
  "expireddate" >  to_date('2020-06-13’)
  ```
  * Reproject business licenses
  * Extract points within analyzed boundary
  * Buffer business without dissolve (50)
  * Save Businesses to GeoPackage
