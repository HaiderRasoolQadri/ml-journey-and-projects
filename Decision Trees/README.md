## Decision Trees — Definition, Intuition, Types, Mathematical & Geometric Intuition

### 1. Definition of Decision Tree and Its Working Intuition

A Decision Tree is a supervised learning algorithm used for both classification and regression tasks.
It works by recursively splitting the dataset into subsets based on feature values to create a tree-like model of decisions.

Each:

- Internal node represents a test on a feature (e.g., Age > 30),
- Branch represents the outcome of that test,
- Leaf node represents a final prediction (either a class label or a numerical value).

**Working Intuition**

The core idea is to find splits that produce subgroups as pure as possible — meaning each subgroup contains similar outcomes.

Steps:

1.  Start with the entire dataset at the root node.
2.  Choose a feature and threshold that best splits the data (based on impurity reduction).
3. Recursively apply the splitting to each child node.
4. Stop when the data is pure or a stopping condition (e.g., max depth) is reached.

In simple terms, the tree keeps asking ``if–else`` questions that divide the data into smaller homogeneous groups, until a clear decision (prediction) can be made.

## 2. Types of Decision Trees

1. Classification Tree
2. Regression Tree

## 3. Decision Tree for Classification
### 3.1  Mathematical Intuition

For classification, the goal is to create nodes that contain samples belonging to a single class as much as possible.

Let the dataset at a node contain 𝑛 samples distributed across 𝑘 classes.

Let $p_i$ denote the proportion of samples belonging to class 𝑖.

**1. Entropy (Information Gain)**

Entropy measures the impurity (uncertainty) of a dataset:

$$H(S) = - \sum_{i=1}^{k} p_i log_2(p_i)$$

If a node is pure (all samples belong to one class), 𝐻(𝑆) = 0

If the samples are equally distributed, H(S) is maximum.

When we split on a feature A, the Information Gain (IG) is:

\[
IG(S, A) = H(S) - \sum_{v \in \text{values}(A)} \frac{|S_v|}{|S|} H(S_v)
\]

The feature with the highest IG is chosen for splitting.

**2. Gini Index - CART**

\[
Gini(S) = 1 - \sum_{i=1}^{k} p_i^2
\]

A lower Gini value indicates a purer node.

The split minimizing Gini impurity is chosen.
### 3.2 Geometric Intuition

Geometrically, a classification tree divides the feature space into axis-aligned rectangles (regions).

Each split corresponds to a line (for 2D) or a plane (for higher dimensions) that separates data points of different classes.

The final tree forms non-overlapping decision regions, each assigned to the majority class of samples inside it.

In essence, the model builds a piecewise constant approximation of the decision boundary.

## 4. Decision Tree for Regression

### 4.1 Mathematical Intuition

For regression, the target variable is continuous.
The aim is to create partitions where the target values are as close to each other as possible.

At a node with 𝑁 samples having target values $y_1, y_2, y_3, ..., y_N$

Mean Squared Error (MSE) Criterion

$$MSE = \frac{1}{N} \sum_{i=1}^{N} (y_i - \bar{y})^2$$

where $\bar{y}$ is the mean of target values in that node.

The algorithm evaluates all possible splits and selects the one that minimizes the weighted MSE after the split:

$$MSE_{split} = \frac{N_L}{N} MSE_{L} + \frac{N_R}{N} MSE_{R}$$

### 4.2 Geometric Intuition

A regression tree divides the feature space into rectangular regions, and each leaf region is assigned a constant value equal to the mean of the target values within that region.

Geometrically, this creates a piecewise constant approximation of the true function — like a staircase function that adjusts to data variations locally.