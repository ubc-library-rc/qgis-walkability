---
layout: default
title: Process
nav_order: 5
parent: Network Analysis
---

# Pre-processing 
Before we can perform spatial network analysis we first must run some geoprocessing on

- urban-blocks.geojson
- street-network.geojson
- business-licenses.geojson

Pre-processing refers to any manipulating or layer creation you do with your base dataset in order to prepare inputs for your network analysis model. For example, editing attribute tables and fixing geometries, clipping layers to an area of interest, re-projecting etc. 

To skip this step you may find the pre-processed data in the workshop-data subfolder called **pre-processed**. However, if you have the time, processing the data yourself will exercise your geoprocessing skills and provide continuity to your workflow. Projects outside of this workshop will likely require you to pre-process datasets yourself, so it's useful to practice with guided instructions. 
{: .note}

---
*Until specified, all geoprocessing may be run with outputs left as temporary files.*

<!-- *1*{: .circle .circle-purple}  **Process street-network: get intersections** -->
<br>
<span style="font-size:15px;"> Process street network: get intersections</span> 
{: .label .label-step}

* Run the **Line Intersections** tool on <i>street-network</i>. You can find it under Vector --> Analysis Tools, or simply by searching for it in the Help menu at the top of your screen. Both the Input and Intersection layer will be <i>street-network</i>.    
* On the resulting <i>Intersections</i>, run a 15m <b>Buffer</b> selecting the option to **Dissolve result** 
* Convert  the resulting <i>Buffered</i> from <b>Multipart to singleparts</b> using the tool by that name. Find it under Vector --> Geometry Tools, or by searching the Help menu.    
* Find <b>Centroid</b> of <i>Singlepart parts</i>. The Centroid tool is also under Vector --> Geometry Tools.
<br><br>
![intersections-vs-centroids](./images/intersections-vs-centroids_20230219.jpg)    

* Export the resulting <i>Centroids</i> as ***street-intersections*** in GeoJSON format to your workshop-data folder.
* Remove all temporary layers and save your QGIS project
<!-- * <b>Extract by locations</b> intersections (within boundary unce. boundary isnt aerial buffer? if so, would have had to find centroids of intersections within that area - this step is unclear whether it wants intersections or buffer centroids - going with centroids for now) maybe can just skip this?  -->
{: .step}

    
<br>
<span style="font-size:15px;"> Process urban blocks: get centroids</span> 
{: .label .label-step}

* Run the <b>Centroid</b> tool on *urban-blocks*    
* <b>Buffer (800m)</b> <i>Centroids</i> with the <b>dissolve</b> option selected. This merges overlapping buffer areas, returning the outer contour of all buffers rather than the set of buffers around each block's centroid.    
* Export both output layers *Centroid* and *Buffer* to your workshop-data folder in .geoJSON format, named ***block-centroids*** and ***boundary*** respectively. Save your project and remove temporary files.<br>       
![Preprocess samples](./images/block-centroids_20230220.jpg)
{: .step}

    

<br>
<span style="font-size:15px;"> Process business licenses</span> 
{: .label .label-step}

* Add business-licenses.geojson to your map canvas. It may take a while for the layer to load because it is nearly 450 megabytes. For the purposes of this workshop we want only the set of businesses that are retail dealers and have a valid (non-expired) license. Let's run some expressions to select businesses based on these parameters...    

* Open the attribute table of *business-licences*. It will take a moment to load over 300,000 features.     

* Open <b>Select by expression</b>. In the middle panel of the dialogue box is a list of input options. Expand **Fields and Values**, **Date and Time**, and **Operators**    

* To select only valid licences, double-click the Field *expireddate*, then the **>** Operator, then **to_date** from the Date and Time functions, and enter today's date in single quotes inside the parentheses.    
```
"expireddate" >  to_date('2023-04-05’)
```    

* We can select for walkability-related businesses in the same expression. Double click the AND Operator and, from the bottom of the expression builder, an open bracket. We are interested in retail businesses that are food and drink related. Enter the following values for the field *businesstype* using the = and or Operators. Make sure to enter *businesstype* for each value. Close the bracket. Your Expression should look as follows:
```sql
"expireddate" > to_date('2023-04-05')  AND  
("businesstype"  =  'Retail Dealer' or 
"businesstype" =  'Retail Dealer - Food' or  
"businesstype"  = 'Retail Dealer - Grocery')
```
* Click *select features* at the bottom right of the dialogue box to run your query. Once the selection has run, return to your attribute table. Your expression should select 1920 features. You can choose to view only selected features from the bottom left corner of your attribute table.
* Return to your QGIS interface. Export *selected features* from the *business-licences* layer. Set the CRS to that of the project (EPSG:26910) and keep the output format GeoJSON. Save the layer to your workshop-data folder and name it ***businesses***.    

* Remove *business-licences* from your Layers panel. 
![selected-businesses](./images/selected-businesses_20220405.jpg)
{: .step}

--- 
You should now have the following additional layers in your workshop-data folder:

- street-intersections
- block-centroids
- boundary
- businesses

These processed layers will be used in the network analysis we will perform next. We will also use the following layers already provided: 

- street-network
- urban-blocks
- census-DAs

**If you have all these layers, continue to the next section.** If not, review the documentation above, or find the layers you need in the *pre-processed* folder of your workshop-data. 
