#  DBSCAN Algorithm (Density-Based Spatial Clustering of Applications with Noise)
---
## What is DBSCAN?
**DBSCAN** stands for **Density-Based Spatial Clustering of Applications with Noise**.  
It is a **density-based clustering algorithm** that groups points that are close to each other (high density areas) and marks isolated points in low-density areas as **outliers (noise)**.  

Unlike K-Means, DBSCAN **does not require specifying the number of clusters** beforehand — it discovers clusters automatically.

##  How DBSCAN Works
DBSCAN defines clusters as **areas of high density separated by areas of low density**.  
It starts from an arbitrary point and expands clusters by including all **density-connected points**.  
Points that cannot be reached by any cluster are labeled as **noise**.

## Key Hyperparameters

| Parameter | Symbol | Description |
|------------|----------|-------------|
| Epsilon | `ε` | The maximum radius of the neighborhood around a point. |
| Minimum Points | `MinPts` | The minimum number of points required to form a dense region (including the point itself). |

##  Types of Points

| Type | Description |
|------|--------------|
| **Core Point** | A point with **at least `MinPts`** points (including itself) within radius `ε`. |
| **Border Point** | A point that is **reachable from a core point**, but **not a core point** itself (doesn't have enough neighbors). |
| **Noise** | A point that is **not reachable** from any core point (isolated). |

##  Density Concepts

- **Directly Density-Reachable:**  
  Point `p` is directly density-reachable from point `q` if `p` is within distance `ε` of `q`, and `q` is a **core point**.

- **Density-Reachable:**  
  Point `p` is density-reachable from `q` if there exists a chain of points `p1, p2, …, pn` where each is directly density-reachable from the previous one.

- **Density-Connected:**  
  Two points `p` and `q` are density-connected if there exists a point `o` such that both `p` and `q` are density-reachable from `o`.

##  DBSCAN Algorithm Steps

1. Choose an unvisited point `p`.
2. Find all points within distance `ε` from `p` (its neighborhood).
3. If the neighborhood has **fewer than `MinPts`**, mark `p` as **noise** (temporarily).
4. If the neighborhood has **at least `MinPts`**, create a new **cluster**.
5. Expand the cluster:
   - Add all points in `p`’s neighborhood to the cluster.
   - For each new point that is a **core point**, add its neighbors to the cluster.
   - Continue until no new points can be added.
6. Repeat until all points are visited.

##  Advantages

- **No need to specify the number of clusters** (unlike K-Means).  
- Can find **arbitrarily shaped clusters**.  
- **Detects outliers (noise)** naturally.  
- Works well when clusters are **dense and well-separated**.

##  Disadvantages

- Choosing good values for `ε` and `MinPts` is **non-trivial**.  
- Performs poorly if clusters have **varying densities**.  
- Can be **slow** on large datasets (due to distance calculations).  
- Struggles in **high-dimensional spaces**.
