# K-Means Clustering — Complete Guide
---
## What is K-Means Clustering?

**K-Means Clustering** is an **unsupervised machine learning algorithm** used to group similar data points into **K clusters**.  
The goal is to **minimize the distance** between data points and their corresponding **cluster centers (centroids)**.

> It divides data into K groups such that points in the same group are more similar to each other than to those in other groups.

##  How K-Means Works (The 5 Steps)

**Step 1: Choose the number of clusters (K)**

This can be based on prior knowledge or determined using methods like the **Elbow Method** or **Silhouette Score**.

**Step 2: Initialize centroids**

Randomly select K data points as the **initial cluster centers (centroids)**.

**Step 3: Assign points to the nearest centroid**

Each data point is assigned to the cluster whose centroid is **closest**  
(commonly measured using **Euclidean distance**).

**Step 4: Update centroids**

Recalculate the centroid of each cluster as the **mean** of all the points assigned to it.

**Step 5: Repeat until convergence**

Repeat Steps 3 and 4 until:
- Centroids do not change significantly, or  
- A maximum number of iterations is reached.

At this point, the clusters are stable.

##  How to Decide the Number of Clusters (K)

Choosing the right **K** is crucial — too few clusters oversimplify the data,  
while too many clusters can lead to overfitting or meaningless groupings.

Two popular methods are:

1. **Elbow Method**
2. **Silhouette Score**

## 1. The Elbow Method

The **Elbow Method** helps find the optimal number of clusters (K) by plotting:

> **K (x-axis)** vs. **Sum of Squared Errors (SSE)** or **Inertia (y-axis)**

- **SSE (Inertia)** measures how close the data points are to their cluster centroids.  
  Lower SSE means better (tighter) clusters.


**Steps:**
1. Run K-Means for a range of K values (e.g., K = 1 to 10).
2. Record the **SSE** for each K.
3. Plot **K vs. SSE**.
4. Look for the “elbow” — the point where the rate of decrease sharply changes.

## 2. Silhouette Score (Alternative)

The **Silhouette Score** is another popular method to evaluate clustering quality.

It measures how similar a data point is to its own cluster (cohesion) compared to other clusters (separation).

**Formula:**
\[
S = \frac{b - a}{\max(a, b)}
\]
Where:
- **a** = average distance between a point and all other points in the same cluster  
- **b** = average distance between a point and points in the nearest cluster

**Score Range:**
- **+1** → Point is well matched to its cluster and far from others  
- **0** → Point is on or very close to the decision boundary  
- **–1** → Point may be assigned to the wrong cluster

**How to Use It:**
1. Compute the Silhouette Score for different values of **K** (e.g., 2–10).
2. Choose the **K with the highest average Silhouette Score**.

## Summary

| Step | Description |
|------|--------------|
| 1 | Choose K (initial guess or using Elbow/Silhouette) |
| 2 | Randomly initialize K centroids |
| 3 | Assign points to the nearest centroid |
| 4 | Update centroids based on cluster members |
| 5 | Repeat until centroids stabilize |

**Choosing K:**
- Use **Elbow Method** to find where SSE stops decreasing sharply  
- Use **Silhouette Score** to find the K with the best cluster separation

## When to Use K-Means

Use K-Means when:
- Data is continuous and numeric
- Clusters are roughly spherical and well-separated
- You need a fast, scalable method for large datasets
- You have a rough idea of K or can estimate it (e.g., with Elbow/Silhouette)
- You want simple, interpretable clusters

## When Not to Use K-Means

Avoid K-Means when:
- Data has categorical or mixed features
- Clusters are non-spherical or unevenly sized
- There are many outliers
- The data contains strongly varying densities
- You don’t know or can’t estimate K meaningfully