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

## Second part of the project
1. Change the label encoding of the semaphore, eg, from ["class 1", "class 2", "class 3"] to [ 1,2,3]

The SEMAFORO feature has the following names that represent the quality of the water. "VERDE","AMARILLO","ROJO".

The label need to be changed to 1, 2 ,3.This is mandatory because for the model to be trained it is necessary to have everything in values.
To achive this get dummies is used. get dummies is used to change cathegorical variables into binary/dummy variables, that later willbe use for machine learning.

![Capture](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/0f213704-82c6-4cc3-a3cc-c9b35fa52be9)

2. Select the X and Y variables. 
![Capture2](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/e2ed0c21-1dc4-46cf-885b-405245a6c16d)


*X: This represents your input features or independent variables.
*y: This represents your target variable or dependent variable.
*test_size: This specifies the proportion of the dataset that should be allocated to the testing set. In the given example, the testing set will be 20% of the entire dataset.
*random_state: This parameter is used to seed the random number generator, which ensures that the data split is reproducible. Setting it to a specific value (in this case, 0) ensures that the same split will be generated if the code is run multiple times.
After executing the train_test_split function, the dataset will be divided into four separate datasets:

*X_train: This will contain a subset of the input features (X) that will be used for training your model.
*X_test: This will contain a subset of the input features (X) that will be used for testing the trained model's performance.
*y_train: This will contain the corresponding subset of target variables (y) for the training data.
*y_test: This will contain the corresponding subset of target variables (y) for the testing data.

3.  Now a feature importance analysis is required, with the most important features.
4.  The features presented below represent the 60% of importance to predict the target.
  
![Capture3 five most predictive features](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/e81ea468-4121-4524-9000-0cb2d4466842)
5. Now with the most important features of the dataset, a new smaller dataset is created and it is used to explore the best classifier between Random Forest and decision tree.

6. Now the precision vs recall for the Random Forest.
6.0.1. Recall, also known as sensitivity or true positive rate, is a performance metric used to evaluate the effectiveness of a classification model. It measures the proportion of actual positive cases that are correctly identified by the model.
 * True Positives (TP): The number of positive cases in the dataset that are correctly predicted as positive by the model.
 * False Negatives (FN): The number of positive cases in the dataset that are incorrectly predicted as negative by the model.
 ** Recall = TP / (TP + FN)
 * A high recall value indicates that the model is effective at capturing positive cases, meaning it has a low rate of false negatives. Conversely, a low recall value suggests that the model is missing a significant number of positive cases and has a high rate of false negatives.
6.0.2. Random forest is like going to a picnic or not, based on some factors like weather, temperature, and wind speed. Instead of relying on a single person's opinion, you decide to ask multiple people and then make your decision based on the majority. It combines the opinions of multiple decision trees to make more accurate predictions.
 * Each decision tree in a Random Forest is trained on a random subset of the data. For example, if you have 100 data points, each tree may be trained on a different 80% of the data, randomly chosen. This process is known as bootstrapping.
 * Additionally, at each decision point in a tree, instead of considering all the available factors, Random Forest randomly selects a subset of factors. This randomness helps to ensure that different trees focus on different aspects of the data and reduces the correlation between the trees.
 * Once all the trees are trained, when you want to make a prediction for a new data point (e.g., whether to go for a picnic or not), each tree gives its own prediction. In the case of classification, the final prediction is determined by majority voting, where the class with the most votes across all the trees is chosen. In the case of regression, the predictions of all the trees are averaged to obtain the final prediction.
6.0.3. A decision tree is like a flowchart that asks a series of questions to classify or predict something. In our example, a decision tree may ask questions like "Is the weather sunny?" or "Is the temperature above 25 degrees Celsius?" Based on the answers to these questions, it reaches a final decision.
 * To build the decision tree, the algorithm looks at the data and decides which question is the best to ask at each step. It tries to pick questions that separate the data into more homogeneous groups, so you can make more accurate decisions.
 * However, sometimes decision trees can become too complex and overfit to the training data, which can lead to poor performance on new data.
 * When a model overfits, it essentially memorizes the training data instead of generalizing from it. As a result, it may have high accuracy or low error on the training data, but it fails to perform well on new data because it has not learned the true underlying patterns.
6.1. In this chart, the Random Fprest precision vs recall curve can be seen.
![Capture4 randoforest vs recall](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/407d8c79-6d16-4790-a529-e7a82787514a)
6.2 An here are the cocnfusion matrix for AMARILLO, ROJO AND VERDE

![Capture6matriz confusion random forest](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/fc08faf8-6cd1-49ac-9fe2-abee511e25d9)
![Capture7 matriz de confusion](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/b10d7478-94b5-4102-9312-3c5b11cb25d5)
![Capture8 Matriz de confusion PNG](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/ecce3d14-c813-4704-9e1b-819b37ac13ab)

6.3 In this chart, the decision tree precision vs recall curve can be seen.
![Capture5 decision tree vs recallPNG](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/23c4f72c-6719-47f5-a90c-21a95e9b72c0)
6.4 An here are the cocnfusion matrix for AMARILLO, ROJO AND VERDE

![Capture9amtriz de confusion decision tree](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/98772ec7-c33a-48d4-a834-763d670d549b)
![Capture11 matriz ocnfusion decision tree](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/15ab86e6-cb15-40c7-840c-259cbcebcc20)
![Capture12Matriz de confusion decision tree](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/abf77c59-242f-4246-aac6-214360b96a7c)
6.5 Comparative table of score for the Random Forest  and the decision Tree.

This is for the Random Forest:

![f1 score](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/e983a81a-8c15-4e3f-8866-39244e0150b3)

And this is for the decision Tree:
![f1 score decision tree](https://github.com/kevin343/Machine-learning-model-for-Underground-Water-Quality./assets/113644566/f511ee1d-6194-433f-a574-5d8163d45e43)
6.6 Conclusion

* For the two classifiers, based on the information provided by the confusion matrices and the recall vs precision charts for both classifiers. Can be concluded that the Random Forest is more precise because it has a higher recall and better precision. with 96%.
* But respect to the score for any of the classifiers is really high and if the dataset were bigger it would be lower. 
