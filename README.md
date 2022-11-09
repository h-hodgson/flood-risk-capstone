# Flood Risk Prediction in southeast England

I completed this project as part of the 12-week immersive data science bootcamp with General Assembly in October 2021. The aim was to **predict flood risk** using factors such as **topology, rainfall, land use, and previous flooding events** from a variety of different data sources. 


## Method

From literature, I concluded that the most suitable method for my project would be to **overlay different layers** (for example, land use, rainfall, etc.) using **QGIS** so that the entire area of interest would have five data points attributed to each site.
- Altitude
- Gradient
- Annual rainfall
- Land cover (split into 20 groups: urban, agricultural, forests, etc.)
- Distance to the nearest river or the sea

|![Land use and contour lines in Tower Hamlets](/landuse_contour.png?raw=true)|
|:--:|
|<b>Land use and contour lines in Tower Hamlets</b>|

I would be predicting whether a flood will happen in future at any particular site and so **the model would be trained on data from previous flooding events** ie. the model would know whether at any particular point a flood had occurred previously or not.

|![Topology and water/land barrier in region of interest](/centroids.png?raw=true)|
|:--:|
|<b>Southeast England showing water boundaries, previous flooding events and topology</b>|   


Training data points were randomly selected across my area of interest in southeast England. The points in the above image are the centroids of the previous flooding events and are not the randomly selected training points!

## Results

After training the model on 3000 data points across southeast England, the best model was then used to build a picture of the predicted flood risk in the whole area of interest **using future rainfall data** predicted by Centre for Environmental Data Analysis. This is visualised in the two images below: the first image showing the current risk and the second showing the increased risk with 10% more rainfall per year.

|![Current flood risk](/final-points-data.png?raw=true)|
|:--:|
|<b>Current flood risk in SE England</b>| 

|![Future flood risk](/future-risk.png?raw=true)|
|:--:|
|<b>"Future" flood risk in SE England</b>| 

With reasonable clarity, the second image is darker than the first image, visualising the heightened risk of flooding with ten percent more annual rainfall across the whole of southeast England.

## Limitations

There were plenty of limitations in this project, from the fact that annual rainfall is far worse an estimator of a flood than the intensity of rain at individual events, to the necessity of using the proximity of the data points to the nearest centroid of a flooding event as the binary yes/no that the area had previously flooded.

However, I was satisfied that ten percent more annual rain did in fact increase the risk of flooding according to my model as it seemed intuitive to me and implied that something was working!

This project was an enjoyable entry into QGIS and ArcGIS and there is a lot more that I'd be interested in doing, perhaps like modelling for an increase in sea level by dropping the altitude by 50 cm, or accounting for flood defences which have been erected since historical flooding events.

### Data Sources recognition

I was able to use a variety of data all from free sources. Thanks goes to:
- Ordnance Survey for topological data
- The Centre for Environmental Data Analysis for rainfall data
- Environment Agency for previously recorded flood outlines
- UKCEH for land cover data

