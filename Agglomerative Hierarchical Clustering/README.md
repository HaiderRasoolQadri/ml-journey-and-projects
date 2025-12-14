# Hierarchical Clustering — Complete Guide
---
##  1. What is Hierarchical Clustering?

**Hierarchical Clustering** is an **unsupervised machine learning** algorithm that groups similar data points into clusters based on their **similarity (distance)**.  
It builds a **hierarchical tree structure** called a **dendrogram**, showing how clusters are merged or divided at different similarity levels.

##  2. Types of Hierarchical Clustering

Hierarchical clustering has two main types:

**a) Agglomerative Clustering (Bottom-Up)** *Most commonly used*
- Starts with **each data point as its own cluster**.
- Repeatedly **merges the two closest clusters** until all points belong to a single cluster.
- The process is visualized using a **dendrogram**.

**b) Divisive Clustering (Top-Down)**
- Starts with **one big cluster** containing all points.
- Recursively **splits** the clusters until each point becomes its own cluster.
- Less commonly used due to high computational cost.

##  3. Working of Hierarchical Clustering (Agglomerative Example)

**Steps:**
1. **Start**: Treat each data point as an individual cluster.  
2. **Compute Distances**: Calculate pairwise distances between clusters using a metric (e.g., Euclidean).  
3. **Merge Clusters**: Combine the two clusters that are closest to each other.  
4. **Update Distances**: Recalculate distances between the new cluster and others (based on linkage type).  
5. **Repeat**: Continue merging until only one cluster remains.  
6. **Visualize**: Draw a **dendrogram** to show the merging process.

##  4. Linkage Criteria (Types of Agglomerative Clustering)

The **linkage criterion** defines how distances between clusters are measured.

| Linkage Type | Description | When to Use |
|---------------|-------------|-------------|
| **Single Linkage** | Distance between the **closest points** of two clusters | Good for **long, chain-shaped** clusters, but **sensitive to outliers** |
| **Complete Linkage** | Distance between the **farthest points** of two clusters | Produces **compact, spherical** clusters; less affected by outliers |
| **Average Linkage** | Average distance between all pairs of points from both clusters | Balanced; works well in most scenarios |
| **Ward’s Method** | Merges clusters to **minimize within-cluster variance (SSE)** | Similar to K-Means; best for **compact, equal-sized clusters** |

## 5. Why Prefer Agglomerative over Divisive

| Reason | Explanation |
|--------|--------------|
| **Efficiency** | Agglomerative is faster — O(n²) vs. Divisive’s O(2ⁿ) |
| **Simplicity** | Easier to understand and implement |
| **Interpretability** | Works naturally with dendrograms |
| **Practical Use** | Divisive is computationally expensive and rarely used in practice |

## 7. Deciding the Best Number of Clusters (K)

Once the dendrogram is built, you can decide **K** using different methods.

**a) Dendrogram “Cut” Method**
- Plot the dendrogram.  
- Look for the **largest vertical distance (gap)** that does not cross any horizontal merge lines.  
- Draw a **horizontal line** across that gap.  
- The number of intersected vertical lines = **optimal number of clusters (K)**.

**b) Distance Threshold Method**
- Define a **distance (height)** threshold.  
- Clusters are formed by cutting the dendrogram at this distance.
  
**c) Silhouette Score**

- Compute the **Silhouette Score** for various values of K.  
- The **K** with the **highest Silhouette Score** represents the best clustering structure.

## 8. Limitations of Hierarchical Clustering

| Limitation | Explanation |
|-------------|--------------|
| **Computationally expensive** | O(n²) complexity — unsuitable for very large datasets |
| **Sensitive to noise/outliers** | Outliers can distort distance calculations and form their own clusters |
| **Irreversible merges/splits** | Once two clusters are merged, they can’t be undone |
| **Metric dependency** | Choice of distance metric (e.g., Euclidean, Manhattan) can change results |
| **Subjective interpretation** | Choosing where to “cut” the dendrogram can be arbitrary |
| **No objective optimization** | Unlike K-Means (which minimizes SSE), it doesn’t have a clear cost function |


