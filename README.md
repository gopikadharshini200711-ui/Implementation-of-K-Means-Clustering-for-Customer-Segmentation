# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Choose K (number of clusters).

2. Initialize centroids randomly.

3. Assign points to nearest centroid.

4. Update centroids until no change

## Program:
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
data = pd.read_csv("/content/Mall_Customers (1).csv")
print(data.head())
print(data.info())
print(data.isnull().sum())
wcss = []
for i in range(1, 11):
kmeans = KMeans(n_clusters=i, init="k-means++", random_state=42)
kmeans.fit(data.iloc[:, 3:5])
wcss.append(kmeans.inertia_)
plt.plot(range(1, 11), wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
km = KMeans(n_clusters=5, random_state=42)
km.fit(data.iloc[:, 3:5])
y_pred = km.predict(data.iloc[:, 3:5])
data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"],
c="red", label="Cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"],
c="black", label="Cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"],
c="blue", label="Cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"],
c="green", label="Cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"],
c="magenta", label="Cluster 4")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.title("Customer Segments")
plt.legend()
plt.show()
```

## Output:
<img width="1352" height="797" alt="Screenshot 2026-03-19 180800" src="https://github.com/user-attachments/assets/f14c81e2-7926-49bf-a938-921d5c94d35e" />
<img width="1091" height="553" alt="Screenshot 2026-03-19 181033" src="https://github.com/user-attachments/assets/a7a36b7b-2fee-4747-84cd-f66dcf585bbc" />
<img width="1053" height="586" alt="Screenshot 2026-03-19 181243" src="https://github.com/user-attachments/assets/d0d85ab5-0cdd-413b-afa7-8d70fceb5f94" />





## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
