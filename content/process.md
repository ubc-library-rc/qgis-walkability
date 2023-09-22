---
layout: default
title: Process
nav_order: 5
parent: Network Analysis
---

# Pre-processing 
Pre-processing refers to any modifications to your given dataset in preparation for network analysis. For example, the workshop data has already been clipped to the area of interest, a pre-processing step you now don't have to worry about. Before performing a network analysis, however, there is some pre-processing to do.     
    
* First, we will create a layer of street intersections from *street-networks* that is simplified so as to account for only one intersection at each crossroad. 
* Then we'll create a point layer from *urban-blocks* that contains the centroid of each block polygon. 
* Finally, we'll create a new layer from *business-licences* that contains only retailers with a valid (non-expired) license. 


To skip this step you may find the pre-processed data in the workshop-data subfolder called **pre-processed**. However, if you have the time, processing the data yourself will exercise your geoprocessing skills and provide continuity to your workflow. Projects outside of this workshop will likely require you to pre-process datasets yourself, so it's useful to practice with guided instructions. 
{: .note}

---
The geoprocessing and analysis tools for vector layers can be found in the **Vector** menu at the top of your screen. Alternatively, you can open the Toolbox panel from the **Processing** menu and search for all tools as needed. Lastly, if you ever are unable to find a tool or any other item in QGIS, try searching it from the **Help** menu. In what follows, *Until specified, the outputs of all geoprocessing may be left as temporary files.*

# Process street network: get intersections    
        

*1*{: .circle .circle-purple} Run the **Line Intersections** tool on <i>street-network</i>
  
>Input layer: <i>street-network</i>    
>Intersection layer: *street-network* 

*2*{: .circle .circle-purple} **Buffer (15m)** the resulting <i>Intersections</i> layer and **Dissolve result** 

*3*{: .circle .circle-purple} Convert the resulting <i>Buffered</i> layer from <b>Multipart to singleparts</b> using the tool by that name

*4*{: .circle .circle-purple} Find the <b>Centroids</b> of <i>Singlepart parts</i> 

*5*{: .circle .circle-purple} Export the resulting <i>Centroids</i> layer. Save as ***street-intersections*** in GeoJSON format to your workshop-data folder. Remove all temporary layers and save your QGIS project.
<br><br>
![intersections-vs-centroids](./images/intersections-vs-centroids_20230715.jpg)    


    
<br>

# Process urban blocks: get centroids 
    
- Run <b>Centroids</b> on *urban-blocks* 
    * save the output as ***block-centroids*** to your workshop-data folder in .geoJSON format
![block-centroids](./images/block-centroids_20230715.jpg)  
 

<br>

# Extract valid business licenses by type

Add *business-licenses.geojson* to your map canvas. It may take a moment to load. For the purposes of this workshop we are only interested in the set of businesses that are retail dealers and have a valid (non-expired) license. Let's run some expressions to select businesses based on these parameters...    

*1*{: .circle .circle-purple} **Open the attribute table**. This will take a moment as well since nearly 300,000 features are being loaded.

*2*{: .circle .circle-purple} Open <b>Select by expression</b>. In the middle panel of the dialogue box is a list of input options. Expand **Fields and Values**, **Date and Time**, and **Operators**    

* To select only valid licences, double-click the Field *expireddate*, then the **>** Operator, then **to_date** from the Date and Time functions, and enter today's date in single quotes inside the parentheses.    
```
"expireddate" >  to_date('2023-07-18')
```    
* We can select for walkability-related businesses in the same expression. Double click the AND Operator and, from the bottom of the expression builder, an open bracket. We are interested in retail businesses that are food and drink related; that is, retail dealers of food or grocery. Enter the following values for the field *businesstype* using the `=` and `or` Operators. Make sure to enter *businesstype* for each value. Close the bracket.         
Your Expression should look as follows:
```sql
"expireddate" > to_date('2023-07-18')  AND  
("businesstype"  =  'Retail Dealer' or 
"businesstype" =  'Retail Dealer - Food' or  
"businesstype"  = 'Retail Dealer - Grocery')
```
* Click **select features** at the bottom right of the dialogue box to run the query. Return to the attribute table. Your expression should select 1463 features. (*Note that the number of selected features will differ depending on the expiration date set.*) Return to the attribute table. You can change the layout view from **Show All Features** to **Show Selected Features** from the bottom left corner of the dialogue box.    

*3*{: .circle .circle-purple} Return to the map canvas. From the layers panel, right click *business-licenses* and go to Export > **Save Selected Features As**
- Keep the output format as GeoJSON
- **Set the CRS to the Project CRS(EPSG:26910 - NAD83/UTM zone 10N)**
- Now save the layer as ***businesses*** to your workshop-data folder
- Remove *business-licences* from the Layers panel
![selected-businesses](./images/selected-businesses_20230715.jpg)


--- 
## Before moving on... 
You should now have the following additional layers in your workshop-data folder:

- *street-intersections*
- *block-centroids*
- *businesses*

These processed layers will be used in the network analysis we will perform next. We will also use the following layers already provided: 

- *street-network*
- *urban-blocks*
- *census-DAs*

**If you have all these layers, continue to the next section.** If not, review the documentation above, or find the layers you need in the *pre-processed* folder of your workshop-data. 
