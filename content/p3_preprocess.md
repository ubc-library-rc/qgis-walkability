---
layout: default
title: workflow
nav_order: 5
parent: Processing
---


Preprocess urban blocks
{: .label .label-step}
* Drag and drop the layers to QGIS
* <b>Reproject</b> layer <i>boundaries</i>
* <b>Reproject</b> layer <i>block_outlines</i>
* <b>Extract by location</b>
  * Extract features from: <i>blocks_reprojected</i>
  * By comparing features from: <i>boundaries_reprojected
* Get <b>Centroid</b> of layer <i>blocks_extracted</i>
* <b>Buffer</b> and dissolve <i>centroids</i> (800m)
* Drag and drop Blocks, Centroids and Boundary to save layers on GeoPackage<br>
![Preprocess samples](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/preprocess_samples.png?raw=true)
{: .step}

Pre process street network
{: .label .label-step}
* <b>Reproject</b> line geometry
* <b>Fix geometries</b> of street centerline layer
* Extract line intersections
* <b>Buffer</b> and dissolve intersections (15m)
* Convert from <b>Multipart to singleparts</b>
* Find <b>Centroid</b> of buffers
* <b>Extract by locations</b> intersections within boundary
* Drag and drop <i>intersections</i> to save layer on GeoPackage<br>
![Preprocess streets](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/preprocess_intersections.png?raw=true)
{: .step}

Pre process dissemination area
{: .label .label-step}
* Open census DA
* <b>Fix geometries</b> from census polygon
* <b>Extract by location</b> DAs within boundary
* Drag and drop Census to save layer on GeoPackage
{: .step}

Pre process business licenses
{: .label .label-step}
* <b>Extract by expression</b> only valid licenses
```
"expireddate" >  to_date('2020-07-17’)
```
* <b>Extract by expression</b> walkability-related business types
```
"businesstype" = 'Retail Dealer' or "businesstype" = 'Retail Dealer - Food' or "businesstype" = 'Retail Dealer - Grocery' or "businesstype" = 'Retail Dealer - Market Outlet' or "businesstype" = 'Liquor Retail Store'
```
* <b>Reproject</b> business licenses
* <b>Extract by locations</b> points within analyzed boundary
* Drag and drop Businesses to GeoPackage
{: .step}
