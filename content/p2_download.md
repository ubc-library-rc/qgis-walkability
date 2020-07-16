---
layout: default
title: 1. Download
nav_order: 2
---

The first step is to download and install the data and softwares necessary to make the analysis. Urban blocks will be used as samples, so in the end, each block will be scored with a walkability index.

QGIS is an open-source software of Geographic Information Systems for Windows and Mac users. You can [download QGIS for free](https://www.qgis.org/en/site/forusers/download.html).

The geospatial data used in the workshop can be downloaded in .GeoJSON format from the City of Vancouver open data catalogue.

* [Download block outlines](https://opendata.vancouver.ca/explore/dataset/block-outlines/download/?format=geojson&timezone=America/Los_Angeles&lang=en)
* [Download business licenses](https://opendata.vancouver.ca/explore/dataset/business-licences/download/?format=geojson&timezone=America/Los_Angeles&lang=en)
* [Download census dissemination areas](https://opendata.vancouver.ca/explore/dataset/census-local-area-profiles-2016/information/)

The street network can be downloaded from inside QGIS using a plugin called QuickOSM. Open QGIS and create a new blank project. QuickOSM can be downloaded by accessing the "Plugins" tab and clicking on "Manage and Install Plugins...". Search for "QuickOSM" and click on "Install Plugin" at the bottom right of the window.

* Download street network from OSM using [QuickOSM](https://plugins.qgis.org/plugins/QuickOSM/)

To skip the preprocessing step, download [pre processed files](https://github.com/ubc-library-rc/qgis-walkability/blob/master/database) from GitHub.
{: .warn}
