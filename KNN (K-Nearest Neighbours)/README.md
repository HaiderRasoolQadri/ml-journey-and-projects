# K-Nearest Neighbors (KNN)
---
K-Nearest Neighbors (KNN) is a **simple yet powerful supervised machine learning algorithm** used for **classification** and **regression** tasks. It predicts outcomes based on the similarity of new data points to existing data.

## 1. What is KNN?

- **Classification:** Assigns a class based on the **majority vote** of K nearest neighbors.  
- **Regression:** Predicts a value based on the **average** of K nearest neighbors.

**Key Idea:**  
> “A new data point takes the label/value of its nearest neighbors.”

## 2. How KNN Works (Intuition)

1. Plot training data points with known labels.  
2. For a new point, find the **K closest points** using a distance metric:
   - **Euclidean Distance** (most common)  
   - **Manhattan Distance**  
   - **Minkowski Distance**  
3. Assign the **class or value** based on the majority or average of neighbors.

**Example (Classification):**

- K = 3  
- Nearest neighbors: [Red, Blue, Red] 
- Majority class → Red → new point classified as Red

## 3. Choosing the Best K

- **Small K (e.g., 1–3):** Captures fine details, **risk of overfitting**.  
- **Large K (e.g., 20–50):** Smooths predictions, **risk of underfitting**.  

**Tips to select K:**

1. Use **cross-validation** to find the value with highest accuracy.  
2. Heuristic: K ≈ √N where N = total number of data points.  
3. Plot **error vs K** to visualize the optimal value.

## 4. Overfitting vs Underfitting

| Scenario       | Description                            | Typical K Value |
|----------------|----------------------------------------|----------------|
| **Overfitting**    | Captures noise and small fluctuations | Small K (e.g., 1) |
| **Underfitting**   | Too smooth, misses important patterns | Large K (e.g., 50) |

## 5. Limitations of KNN

1. **Computationally Expensive:** Distance computation for all training points at prediction time.  
2. **Curse of Dimensionality:** In high-dimensional spaces, distances lose meaning.  
3. **Sensitive to Outliers and Noise:** Can skew predictions.  
4. **Feature Scaling Required:** Normalization or standardization is necessary.  
5. **Not Ideal for Large Datasets**

