# Clustering With K-Means
```python
# Create cluster feature
kmeans = KMeans(n_clusters=6)
X["Cluster"] = kmeans.fit_predict(X)
X["Cluster"] = X["Cluster"].astype("category")

X.head()
```

```python
sns.relplot(
    x="Longitude", y="Latitude", hue="Cluster", data=X, height=6,
);
```