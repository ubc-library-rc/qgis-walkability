---
layout: default
title: Network Analysis
nav_order: 4
has_children: true
---
# Network analysis 

Network analysis helps answer spatial questions regarding the proximity and connection of points or pathways along a network of lines. For example, network analysis performed on a dataset of city streets might investigate the shortest path between two hospitals given one-way streets and major roads. A walkability index is a quantitative assessment of the relative accessability of amenities within an area. The variable inputs an index will account for depends on the questions being asked, the project's scope, data availability, and a host of other factors. Whether you are evaluating a given visualization or building your own, some questions to ponder are: In what ways do walkability indexes render partial representations? Who and what is *not* accounted for by the data? For example, if it snows in winter and sidewalks and pedestrian crossings are not properly cleared of ice, destinations once within walking/rolling may become inaccessible to inhabitants who use mobility aids to move around. 
    
QGIS provides [a suite of geoprocessing tools](https://docs.qgis.org/3.28/en/docs/training_manual/vector_analysis/network_analysis.html) to support network analysis. This workshop offers a basic workflow for generating a walkability index concerned with the proximity of food and grocery retailers to any point along the network of streets within 300 meters of some such business. In other words, how far would you have to go to get food? Walkability indicators (connectivity of street network, population density, number and variation in businesses) are normalized into z-scores, or the measure of a calculated value's distance from the mean.     
