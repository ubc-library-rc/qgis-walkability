---
layout: default
title: Resources
nav_order: 19
---


## Network Analysis Resources

- [Official QGIS documentation on Network Analysis](https://docs.qgis.org/3.10/en/docs/training_manual/vector_analysis/network_analysis.html)<br>
- [Quick spatial network analysis tutorial using QGIS](https://www.youtube.com/watch?v=WzT9_jMbBDw)<br>
- [City of Vancouver open data catalogue](https://opendata.vancouver.ca/)<br>
- [International comparison of observation-specific spatial buffers](http://ij-healthgeographics.biomedcentral.com/articles/10.1186/s12942-017-0077-9)<br>
- [OSMnx: Python for Street Networks](https://geoffboeing.com/2016/11/osmnx-python-street-networks/)<br>
  <br>

## Downloading OSM Street Networks with QGIS Plugin 
The OSM street networks layer provided pre-processed for this workshop was downloaded from inside QGIS using a plugin called QuickOSM. If you are interested in working with street network data for another location, follow the directions below to download it yourself. 
      
Open QGIS and create a new blank project and connect your workshop-data folder as a favorite directory in the browser panel. Add **census-DAs.geojson** to your map canvas. 

From the **Plugins** menu at the top of your screen, navigate to “Manage and Install Plugins…” In the Plugins dialogue box that opens, first go to Settings and enable experimental and deprecated plugins. Return back to All and search “QuickOSM.” Install the plugin and close the dialogue box. Now click on the **Processing** menu at the top of your screen and open the Toolbox. Search for "QuickOSM." Select "Download OSM data from a query in an extent." In the dialogue box that opens you only need to set an extent and location to save the street networks. From the Extent drop-down menu select "Calculate from Layer" and then **census-DAs.** To save the output as a permanent file, click the ellipses and navigate to your workshop-data folder. Now run the tool; it may take a while.  