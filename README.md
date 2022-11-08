# Flood Risk Prediction in southeast England

I completed this project as part of the 12-week immersive data science bootcamp with General Assembly in October 2021. The aim was to **predict flood risk** using factors such as **topology, rainfall, land use, and previous flooding events** from a variety of different data sources. 


## Method

From literature, I concluded that the most suitable method for my project would be to **overlay different layers** (for example, land use, rainfall, etc.) using **QGIS** so that the entire area of interest would have five data points attributed to each site.

![Land use and contour lines in Tower Hamlets](/landuse_contour.png?raw=true "Land use and contour lines in Tower Hamlets")

I would be predicting whether a flood will happen in future at any particular site and so **the model would be trained on data from previous flooding events** ie. the model would know whether at any particular point a flood had occurred previously or not.

![Topology and water/land barrier in region of interest](/centroids.png?raw=true "Southeast England showing water boundaries, previous flooding events and topology")

Training data points were randomly selected across my area of interest in southeast England, shown above.

## Results

After training the model on 3000 data points across southeast England, the best model was then used to build a picture of the predicted flood risk in the whole area of interest **using future rainfall data** predicted by Centre for Environmental Data Analysis. This is visualised in the two images below: the first image showing the current risk and the second showing the increased risk with 10% more rainfall per year.

![Current flood risk](/final-points-data.png?raw=true "Current flood risk in SE England")

![Future flood risk](/future-risk.png?raw=true "Future flood risk in SE England")

### Data Sources recognition

I was able to use a variety of data all from free sources. Thanks goes to:
- Ordnance Survey for topological data
- The Centre for Environmental Data Analysis for rainfall data
- Environment Agency for previously recorded flood outlines
- UKCEH for land cover data

