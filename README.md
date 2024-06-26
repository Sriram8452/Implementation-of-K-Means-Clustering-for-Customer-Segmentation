# Ex.No.8-Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm:

1.Import the necessary packages using import statement.

2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3.Import KMeans and use for loop to cluster the data.

4.Predict the cluster and plot data graphs.

5.Print the outputs and end the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Sriram G
RegisterNumber: 212222230149
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = [] #Within-Cluster sum of square.
for i in range(1,11):
  kmeans=KMeans(n_clusters = i,init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:
### Dataset:
![image](https://github.com/Sriram8452/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708032/aebc56e7-6882-45d9-a785-8f1ad9f9e313)


### Dataset information:
![image](https://github.com/Sriram8452/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708032/8b819822-aa89-406f-b8dd-61266714ed46)
![image](https://github.com/Sriram8452/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708032/57679007-6f66-4d54-adef-ee797a7baf73)


### Elbow method graph (wcss vs each iteration):
![image](https://github.com/Sriram8452/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708032/74549451-d459-4a8a-90f2-3a3adff48f55)


### Cluster represnting customer segments-graph:
![image](https://github.com/Sriram8452/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708032/11f9db97-0456-4f6b-b911-f3175fdc6fd2)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
