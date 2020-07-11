---
layout: default
title: 2. Preprocess
nav_order: 3
---

Preprocess samples
{: .label .label-step}
* <b><em>Reproject</em></b> boundaries
* <b><em>Reproject</em></b> samples
* <b><em>Extract by location</em></b> samples within boundaries
* Get <b><em>Centroid</em></b> of samples
* <b><em>Buffer</em></b> and dissolve centroids (800m)
* Drag and drop Blocks, Centroids and Boundary layers to GeoPackage
![Preprocess samples](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/preprocess_samples.png?raw=true)
{: .step}

Pre process street network
{: .label .label-step}
* <b><em>Reproject</em></b> line geometry
* <b><em>Fix geometries</em></b> of street centerline layer
* Extract line intersections
* <b><em>Buffer</em></b> and dissolve intersections (15m)
* Convert from <b><em>Multipart to singleparts</em></b>
* Find <b><em>Centroid</em></b> of buffers
* <b><em>Buffer</em></b> intersection to create a polygon
* <b><em>Extract by locations</em></b> intersections within boundary
* Drag and drop Intersections to GeoPackage
![Preprocess streets](https://github.com/ubc-library-rc/qgis-walkability/blob/master/images/preprocess_intersections.png?raw=true)
{: .step}

Pre process dissemination area
{: .label .label-step}
* Open census DA
* <b><em>Fix geometries</em></b> from census polygon
* <b><em>Extract by location</em></b> DAs within boundary
* Drag and drop Census to GeoPackage
{: .step}

Pre process business licenses
{: .label .label-step}
* Filter valid licenses by expression
```
"expireddate" >  to_date('2020-06-13’)
```
* <b><em>Reproject</em></b> business licenses
* <b><em>Extract by locations</em></b> points within analyzed boundary
* <b><em>Buffer</em></b> business without dissolve (50)
* Drag and drop Businesses to GeoPackage
{: .step}
