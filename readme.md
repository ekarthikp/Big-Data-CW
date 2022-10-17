## A Gamut of Locality Approaches for Applying SMOTE+ENN to Big Data
#### TB03 - Techniques to deal with Imbalanced Big Data

To run any of the three approaches, simply open the workbook, update the directory to the dataset if required, and run all cells.

Dataset is in repo and also available here: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

##### Approach 1 - Local_MapReduce
Here we leverage an existing MLib implementation of the k-means algorithm (’k-means ||’) which has been optimised for cluster based workflows by utilizing hybrid spill trees.
![Alt text](https://github.com/ekarthikp/Big-Data-CW/blob/main/Images/Approach%201%20diag.png?raw=true "Approach 1 Diagram")
![Alt text](https://github.com/ekarthikp/Big-Data-CW/blob/main/Images/Approach%201%20algo.png?raw=true "Approach 1 Algorithm")
##### Approach 2 - Smote_Enn_Global

This global approach utilises the LSH to perform SMOTE and ENN in a distributed fashion. It first vectorises the features, before perfoming SMOTE and ENN sequentially and then trains a Random Forest clasifier on the preprocessed data and measures the performance of this classifier.
![Alt text](https://github.com/ekarthikp/Big-Data-CW/blob/main/Images/Approach%202%20diag.png?raw=true "Approach 2 Diagram")
![Alt text](https://github.com/ekarthikp/Big-Data-CW/blob/main/Images/Approach%202%20algo.png?raw=true "Approach 2 Algorithm")
##### Approach 3 - Smote_Enn_Cluster_Global
This global approach first clusters the data using k-means clustering, then performs SMOTE + ENN on these clusters, before they are merged together using union and evaluated using a Random Forest classifier.

![Alt text](https://github.com/ekarthikp/Big-Data-CW/blob/main/Images/SMOTE%2BENN.png?raw=true "Approach 3 Diagram")
![Alt text](https://github.com/ekarthikp/Big-Data-CW/blob/main/Images/SMOTE%2BENN%20approach%203%20algo.png?raw=true "Approach 3 Algorithm")


#### Sources

K Means Clustering
https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.clustering.KMeans.html

Global SMOTE with LSH
https://gist.github.com/hwang018/420e288021e9bdacd133076600a9ea8c 
