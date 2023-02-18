---
layout: default
title: Data
nav_order: 3
parent: Introduction 
---

# Workshop Data 

The first step is to download and install the data and softwares necessary to make the analysis. If you haven't already, download the latest version of QGIS  from [qgis.org](https://qgis.org/en/site/forusers/download.html). Make sure to download the long term release for stable functionality. 

The geospatial data used in the workshop can be downloaded in .GeoJSON format from the City of Vancouver open data catalogue and from Statistics Canada.

* [Download block outlines](https://opendata.vancouver.ca/explore/dataset/block-outlines/download/?format=geojson&timezone=America/Los_Angeles&lang=en)
* [Download business licenses](https://opendata.vancouver.ca/explore/dataset/business-licences/download/?format=geojson&timezone=America/Los_Angeles&lang=en)
* [Download 2021 census dissemination areas](./content/data/census-DAs.geojson)

The street network can be downloaded from inside QGIS using a plugin called QuickOSM. Open QGIS and create a new blank project. 

QuickOSM can be downloaded by accessing the "Plugins" tab and clicking on "Manage and Install Plugins...". Search for "QuickOSM" and click on "Install Plugin" at the bottom right of the window.

* Download street network from OSM using [QuickOSM](https://plugins.qgis.org/plugins/QuickOSM/)

To skip the preprocessing step, download [pre processed files](https://github.com/ubc-library-rc/qgis-walkability/blob/master/database/preprocessed.zip) from GitHub.
{: .warn}
