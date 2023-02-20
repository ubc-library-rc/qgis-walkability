---
layout: default
title: Data
nav_order: 2
parent: Introduction 
---

# Workshop Data 

The first step is to download and install the data and softwares necessary to make the analysis. If you haven't already, download the latest version of QGIS  from [qgis.org](https://qgis.org/en/site/forusers/download.html). Make sure to download the long term release for stable functionality. 

The geospatial data used in the workshop can be downloaded in .GeoJSON format from the City of Vancouver open data catalogue and from Statistics Canada. Street network data is from Open Street Map. 

[Download and extract workshop-data](./content/workshop-data.zip){: .btn .btn-blue }
<br>
( folder not finalized)


<!-- * [Download block outlines](https://opendata.vancouver.ca/explore/dataset/block-outlines/download/?format=geojson&timezone=America/Los_Angeles&lang=en)
* [Download business licenses](https://opendata.vancouver.ca/explore/dataset/business-licences/download/?format=geojson&timezone=America/Los_Angeles&lang=en)
* [Download 2021 census dissemination areas](./content/data/census-DAs.geojson)
* [Download street networks](./content/data/OSM-street-network.geojson) -->



<br>

The data Because datasets like that of all businesses for the entire city are quite large, they require a great deal of time and (your computer's) capacity to process. For this reason, today's workshop focuses on the areas of Vancouver north of Broadway. The data downloaded above is already clipped to this area of interest. If you would like to develop a walkability index for the entire city on your own time, you may download the full datasets here:<br><br>
[Businesses](https://opendata.vancouver.ca/explore/dataset/business-licences/download/?format=geojson&timezone=America/Los_Angeles&lang=en)<br>[OSM Street Networks](./content/data/OSM-street-network.geojson)<br>[Urban-Blocks](https://opendata.vancouver.ca/explore/dataset/block-outlines/download/?format=geojson&timezone=America/Los_Angeles&lang=en)
{: .note}

<!-- Create a folder titled **workshop-data** and drag all the workshop data you just downloaded into it. This will help you stay organized as you work, especially since we will be creating multiple new files during the workshop.
{: .note} -->

<br>

<!-- Optional: Download Street Networks with QGIS Plugin
    
The street network can be downloaded directly from inside QGIS using a plugin called QuickOSM. Open QGIS and create a new blank project and connect your workshop-data folder as a favorite directory in the browser panel. Add **census-DAs.geojson** to your map canvas. 

From the **Plugins** menu at the top of your screen, navigate to “Manage and Install Plugins…” In the Plugins dialogue box that opens, first go to Settings and enable experimental and deprecated plugins. Return back to All and search “QuickOSM.” Install the plugin and close the dialogue box. Now click on the **Processing** menu at the top of your screen and open the Toolbox. Search for "QuickOSM." Select "Download OSM data from a query in an extent." In the dialogue box that opens you only need to set an extent and location to save the street networks. From the Extent drop-down menu select "Calculate from Layer" and then **census-DAs.** To save the output as a permanent file, click the ellipses and navigate to your workshop-data folder. Now run the tool; it may take a while.  -->


