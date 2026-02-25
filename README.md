# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import necessary libraries: pandas for data manipulation and matplotlib.pyplot for visualization.

2.Load the customer data from a CSV file into a pandas DataFrame

3.Perform K-means clustering using sklearn's KMeans algorithm, employing the elbow method to find the optimal number of clusters.

4.Fit a KMeans model with 5 clusters to the data.

5.Predict cluster labels for each data point and add them to the DataFrame.

6.Visualize the customer segments by plotting their annual income against spending score, coloring points by cluster membership.
## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: PARVEEN SULTHANA J
RegisterNumber:  212224040233

import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/Mall_Customers.csv")
data

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  Kmeans=KMeans(n_clusters = i,init = "k-means++")
  Kmeans.fit(data.iloc[:,3:])
  wcss.append(Kmeans.inertia_)
plt.plot(range(1, 11), wcss[:10])
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img width="785" height="621" alt="ML10 1" src="https://github.com/user-attachments/assets/4b8a2418-fde1-4811-b766-5fffd4f94048" />
<img width="770" height="287" alt="ML10 2" src="https://github.com/user-attachments/assets/707b244f-5b74-490a-b2ee-6ad3d73c6fa9" />
<img width="597" height="319" alt="ML10 3" src="https://github.com/user-attachments/assets/6b4d1b6e-ca4f-4084-9943-dada692e00c5" />
<img width="357" height="329" alt="ML10 4" src="https://github.com/user-attachments/assets/1df07b5c-5470-4c5b-b0ca-5ae49adf8335" />
<img width="877" height="566" alt="ML10 5" src="https://github.com/user-attachments/assets/151acd4d-1b32-4ece-b368-e5c7dc3e060f" />
<img width="826" height="546" alt="ML10 6" src="https://github.com/user-attachments/assets/d4a87fe5-28a6-47e0-ba48-08d631fcf6d6" />



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
