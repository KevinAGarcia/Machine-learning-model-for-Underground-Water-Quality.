# Machine-learning-model-for-Underground-Water-Quality.
Prepared and cleaned the dataset to explore tendencies and correlations in Python, Performed and analysis of Feature Importance through Decision Trees and Random Forest.

## About the project

The first part of the project consists of a database that corresponds to worldwide underground and superficial water. Once one of the options is selected there are certain tasks that need to be addressed.

 * Database cleaning. Explore each data (auxiliate of describe(), mean(), plot, pandas boxplot):
 * Identifying average, mean, and median central trends of the data.
 * Identify measures of dispersion, maximum, minimum.Identify non-central position measures, quartiles, outliers.Identify correlations.
 * Prepare the data.Perform analysis to find if there is a relationship between water quality and its geographic location through K-means.

Once the dataset is ready and prepared. The second part of the project is to select dependent X and independent Y for the column "SEMAFORO". SEMAFORO has three options that are referenced to the quality of the water which are bad, medium and great.

* Change the label encoding of the semaphore, eg, from ["class 1", "class 2", "class 3"] to [ 1,2,3]
* Perform a general analysis of important features through decision trees or random forest.
* Make your classifier, remember to divide the data in a balanced way (auxiliate train test split)
* Explore which classifier is the most optimal, example: decision trees Random Forest.
* Determine the degree of accuracy through the classification report https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html .
* Visualize model results or predictions through a confusion matrix.

## First step Cleaning the dataset.

 The dataset that contained many features had many problems because of missing values, corrupted values, so by cleaning the data using mean(), describe() and pandas boxplot the data was completely clean.
 
 ![Capture](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/89e98d06-c3e8-41a4-b4f8-c6543c161569)

 Finally a correlation matrix is presented to determine which features are more importand
 ![Capture2](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/c90b13b4-01a7-4214-a4e2-17b8bba9bb18)

 
## Realizar análisis para encontrar si existe una relación entre la calidad del agua y su ubicación geográfica a través de K- means.

1. Normalize the data. Data is normalized to have everything in the same scale and avoid conflicts Min max() is used to linealize everything beetween [1,0].
   X_norm = (X - X_min) / (X_max - X_min). 
2. Scikit-learn library is imported , which are for machine learning, in this case for classification.
3. Plot the points with the features of Longitud and Latitud.
![Capture mexico points3](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/598a346c-fe05-4c2b-a201-424884997755)
5. To determine the number of clusters the knee or elbow method is used. This method consists of determining for what cluster every point belongs. It is calculated by the distance ower to the 2 beetwen the points and the cluster. The objective of the CSS(cluster sum of squares) is to because this means the points are closer to the centroid.
![Capture3 elbow](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/d2e26db9-83e2-40da-8e71-6c4d6a3775cc)
7. Because of the results it is selected a K = 5 and Plot of mexico is presented with its clusters.
![Capture4 mexico clusters](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/6d398299-021f-4b0d-abb1-bf4b2bc08af2)
9. Now the Geopandas lybrary is used to viusalize geospace data. It this case to plot the mexican country in the map
![Capture5 Mexico](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/b9b6d23d-39b4-4363-9fc7-6bce831d3b3a)

A chart is presented with the 5 clusters and the quality of water showing the clusters that have better quality of water.
![Capture6 chart with cluster and water](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/3806135c-276f-4143-9f8f-05464300529c)
*Green means good quality water
*Yellow meand average quality water 
* Red meand low quality water
## Change the label encoding of the semaphore, eg, from ["class 1", "class 2", "class 3"] to [ 1,2,3]

The SEMAFORO feature has the following names that represent the quality of the water. "VERDE","AMARILLO","ROJO".

The label need to be changed to 1, 2 ,3.This is mandatory because for the model to be trained it is necessary to have everything in values.
To achive this get dummies is used. get dummies is used to change cathegorical variables into binary/dummy variables, that later willbe use for machine learning.

![Capture](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/0f213704-82c6-4cc3-a3cc-c9b35fa52be9)

