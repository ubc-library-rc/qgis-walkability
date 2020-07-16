---
layout: default
title: 2. Preprocess
nav_order: 3
---

Preprocess urban blocks
{: .label .label-step}
* Drag and drop <i>block_outlines.shp</i> to QGIS
* Drag and drop <i>
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
* <b>Buffer</b> intersection to create a polygon
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
"businesstype" != 'Apartment House' and "businesstype" != 'Apartment House Strata' and "businesstype" !=  'Auto Dealer' and "businesstype" != 'Auto Detailing' and "businesstype" != 'Auto Painter & Body Shop' and "businesstype" != 'Auto Parking Lot/Parkade' and "businesstype" != 'Auto Repairs' and "businesstype" != 'Auto Washer' and "businesstype" != 'Bed and Breakfast' and "businesstype" != 'Gas Contractor' and "businesstype" != 'Gasoline Station' and "businesstype" != 'Junk Dealer' and "businesstype" != 'Machinery Dealer' and "businesstype" != 'Manufacturer' and "businesstype" != 'Manufacturer - Food' and "businesstype" != 'Manufacturer - Food with Anc. Retail' and "businesstype" != 'Manufacturer with Anc. Retail' and "businesstype" != 'Rentals' and "businesstype" != 'Repair/ Service/Maintenance' and "businesstype" != 'Residential/Commercial' and "businesstype" != 'Sheet Metal Works' and "businesstype" != 'Warehouse Operator' and "businesstype" != 'Warehouse Operator - Food' and "businesstype" != 'Wholesale Dealer - Food' and "businesstype" != 'Wholesale  Dealer' and "businesstype" != 'Wholesale Dealer - Food with Anc. Retail' and "businesstype" != 'Wholesale Dealer w/ Anc. Retail'
```
* <b>Reproject</b> business licenses
* <b>Extract by locations</b> points within analyzed boundary
* <b>Buffer</b> business without dissolve (50)
* Drag and drop Businesses to GeoPackage
{: .step}
