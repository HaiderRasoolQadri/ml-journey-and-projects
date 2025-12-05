# Support Vector Machine (SVM)
---
## What is SVM?

**Support Vector Machine (SVM)** is a **supervised machine learning algorithm** used mainly for **classification** (and sometimes regression).  
It tries to **find the best separating boundary (hyperplane)** that divides data points of different classes with the **maximum possible margin**.

## Relation to Logistic Regression

Both **SVM** and **Logistic Regression** are **linear classifiers** at their core.

| Aspect | Logistic Regression | SVM |
|--------|----------------------|-----|
| Objective | Finds a boundary that best models **probabilities** of classes (by minimizing log-loss) | Finds a boundary that **maximizes the margin** between classes |
| Output | Gives **probability estimates** | Gives **decision boundary** (no probability by default) |
| Sensitivity to Outliers | More sensitive (since it uses log-loss) | Less sensitive (margin-based) |

So, SVM can be thought of as a **"harder" version** of logistic regression — instead of fitting probabilities, it focuses on the **geometry of separation**.

## Working Intuition of SVM

Imagine you have two classes of points (say red and blue).  
There could be **many lines** that separate them, but SVM wants the **one that’s farthest from both** — i.e., has the **maximum margin**.

- **Margin** = distance between the separating hyperplane and the nearest data points from each class.  
- The data points that lie **on the margin** are called **support vectors**.  
- These **support vectors determine the decision boundary** — other points don’t affect it.
- 
## 1. Hard Margin SVM

- Assumes the data is **perfectly linearly separable**.  
- Tries to find a hyperplane that **completely separates** the classes **without any misclassification**.  
- Formally:

  \[
  \min \frac{1}{2}||w||^2 \quad \text{such that } y_i(w \cdot x_i + b) \ge 1
  \]

- Works only if data is **noise-free** and **linearly separable**.

- **Pros:** Perfect separation  
- **Cons:** Not robust — a single noisy point can make it fail.

## 2. Soft Margin SVM

- Real-world data **is not perfectly separable** — noise, overlaps, etc.  
- **Soft margin SVM** allows **some violations (misclassifications)** by introducing **slack variables (ξᵢ)**.

\[
\min \frac{1}{2}||w||^2 + C \sum \xi_i \quad \text{such that } y_i(w \cdot x_i + b) \ge 1 - \xi_i, \ \xi_i \ge 0
\]

- \( C \) = **regularization parameter**
  - Large \( C \): less tolerance to errors → narrower margin  
  - Small \( C \): more tolerance → wider margin

- **Pros:** Handles noisy data  
-  **Cons:** Needs tuning of \( C \)

## 3. Kernel SVM

What if the data **is not linearly separable** even with soft margins?

We use the **kernel trick** — it maps the data into a **higher-dimensional space** where it becomes linearly separable.

### Common Kernels:
- **Linear kernel** — same as linear SVM  
- **Polynomial kernel** — curved decision boundary  
- **RBF (Gaussian) kernel** — flexible, nonlinear boundary  
- **Sigmoid kernel** — behaves like a neural network

**Example:**  
In 2D, circles can’t be separated by a line — but in 3D, they can be separated by a plane.

##  Pros and Cons of SVM

| Pros | Cons |
|-------|-----------|
Works well in **high-dimensional** spaces  |**Slow training** on large datasets (complex optimization)
Effective even with **small datasets**  |Hard to interpret results 
**Robust** to overfitting (especially with proper kernel & C)  |**Choice of kernel** and parameters (C, γ) crucial
**Mathematically elegant**|Doesn’t output **probabilities** by default (unlike logistic regression)
