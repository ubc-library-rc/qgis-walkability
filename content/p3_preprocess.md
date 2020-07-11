---
layout: default
title: 2. Preprocess
nav_order: 3
---

Preprocess samples
{: .label .label-step}
* Reproject boundaries
* Reproject samples
* Extract samples within boundaries
* Get centroids of samples
* Buffer and dissolve centroids (800m)
* Save Blocks, Centroids and Boundary to GeoPackage
![Preprocess samples](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/preprocess_samples.png?raw=true)
{: .step}

Pre process street network
{: .label .label-step}
* Reproject line geometry
* Fix street line geometries
* Extract line intersections
* Buffer and dissolve intersections
* Convert to single-parts
* Find centroids of buffers
* Buffer intersection to create a polygon
* Extract intersections within boundary
* Save Intersections to GeoPackage
![Preprocess streets](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/preprocess_intersections.png?raw=true)
{: .step}

Pre process dissemination area
{: .label .label-step}
* Open census DA
* Fix census polygon geometries
* Extract DAs within boundary
* Save Census to GeoPackage
{: .step}

Pre process business licenses
{: .label .label-step}
* Filter valid licenses by expression
```
"expireddate" >  to_date('2020-06-13’)
```
* Reproject business licenses
* Extract points within analyzed boundary
* Buffer business without dissolve (50)
* Save Businesses to GeoPackage
{: .step}
