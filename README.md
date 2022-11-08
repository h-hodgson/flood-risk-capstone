# flood-risk-capstone

Flood Risk Prediction in the Southeast of England

Introduction

This project was completed as my Capstone project as part of the twelve week Data Science Immersive course, finishing in October 2021. A project on flood risk appealed to me due to it becoming an increasingly large problem as extreme weather events become more common. The calculation of the risk of flooding in certain areas is important for determining whether it is worth building a house or business in the area, the cost of insuring those already there, and the defences required to protect the land from flooding to save lives.

It is particularly relevant to me as SE England is where I live and I was curious to find out which areas are at higher risk. In the last few months there has been flooding across London, some of it within a couple of miles of my house and so it was a project which might affect my own behaviour. 

Thought Process and Methods

It was assumed that the major factors affecting flooding in the region were altitude and distance from rivers or the sea. This is because it was assumed that rivers and seas would be the source of flooding, from either rivers bursting their banks or surges from the sea during storms. SE England is relatively flat and at a fairly low altitude with the majority of the land less than 50m above sea level and so I assumed that factors such as run-off from hills were of low importance.

The features I used to predict flooding were altitude, slope, land cover type, distance from water source and annual rainfall. Topological data was downloaded from the Ordnance Survey as a Digital Elevation Model. This was a raster layer which contained information about altitude at each pixel at a resolution of 50m. Using the QGIS function Slope, the first derivative of the DEM was calculated to give the slope. 

Annual rainfall data was downloaded from the Centre for Environmental Data Analysis as netCDF (.nc) files on a 12km grid resolution. I took an average of 5 randomly selected years between 1940-2020 using the Raster calculator tool.

Outlines of previously recorded floods were downloaded as a shapefile from the Environment Agency. The shapefile included information detailing the outline of the flood, its area, the date, cause and source among other features. Different outlines were also grouped by the flood event ID, ie. if the different outlines were part of the same ‘flood’.

Land cover data was downloaded from UKCEH. It was a raster file which separated land into 21 categories.

EDA was performed on the recorded flood data to give a general picture of flooding in SE England. The majority of the data was from the post-1940s but some data existed from the 20s and one flood had been recorded from 1707. The sea had been the source of most flooding by area and rivers had been the source of most flooding by number of events. There also appeared to be a lot of flooding due to sewerage around Heathrow Airport and the question was raised as to whether this type of flooding should be included in my modelling.

Prediction

The method for modelling the flood risk of the region was this:
For a large number of points in the region, the five features should be recorded, as well as the distance of the point to the nearest flood.
If the point lay within the bounds of a previous flood, then it would be recorded as flooded in the target column.
Machine learning models would then be built using the data made up of flooded and non-flooded events.

The points were created using the Random points in polygons function and the features were extracted at points using Sample raster values. A plug-in, Nearest Neighbour, was installed and was used to calculate the closest point between each point and the land/water boundary and nearest flood.

The table could then be exported as a csv file and opened in Jupyter Notebooks for modelling in Python. It was this data, along with a target variable of whether the point flooded or not, that was used in the modelling steps.

Modelling

Data containing information about the 3000 randomly selected points was uploaded to Jupyter Notebook. Points which were not thought to be on land were removed from the set by dropping records which had null values.
 
A train-test split was performed on the data and y was stratified as there was a large class imbalance of 91.1 : 8.9 . Different machine learning algorithms were performed as classification models on the data, including logistic regression, k-nearest neighbour, random forest and AdaBoost which had highest r2 scores of 92.5, 94.2, 94.2, 93.1 respectively.
 
This did not mark a significant improvement from the baseline. It was also considered that improving the metric r2 might not be the most desirable and in fact recall might be more useful. As predicting the risk of flooding is as much a safety issue as anything else, it is important to identify all areas which are at risk and so models with high recall are in demand. The logistic regression and knn models has relatively low recalls of 0.24 and 0.67 respectively. It was therefore decided that more modelling was required.
 
A higher recall score was achieved through undersampling. This technique is useful in cases of class imbalances as it trains the model on an equal number of records in each class which essentially means the models does not learn to mostly predict the most common class. While this technique gives a lower overall accuracy (r2 score), the recall of flooded locations increases to 0.95 using a logistic regression classifier. This was the highest test recall achieved by any model using either undersampling or oversampling.
