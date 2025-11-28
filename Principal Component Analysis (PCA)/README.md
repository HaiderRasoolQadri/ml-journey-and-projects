#  Principal Component Analysis (PCA)
---
## 1. Overview

**Principal Component Analysis (PCA)** is a **statistical technique** used to reduce the dimensionality of a dataset while preserving as much variability (information) as possible.  
It transforms a set of **correlated variables** into a new set of **uncorrelated variables** called **principal components (PCs)**, which are ordered by how much variance they capture.

PCA finds new axes (directions) in the data that maximize variance and projects the data onto these new axes.

## 2. Why We Need PCA

High-dimensional datasets often come with redundancy, correlation, and noise. PCA helps by simplifying such data while retaining essential information.

| Problem | How PCA Helps |
|--------------|------------------|
| Correlated features | Produces uncorrelated components |
| High dimensionality | Reduces the number of variables |
| Computational inefficiency | Compresses data into fewer dimensions |
| Visualization difficulty | Enables 2D or 3D visualization |
| Noisy data | Filters out low-variance (noisy) directions |

Thus, PCA is both a **compression** and **noise-filtering** tool.

## 3. Mathematical Intuition

Assume a dataset \( X \in \mathbb{R}^{n \times d} \) where;
\( n \) = number of samples and,
\( d \) = number of features.

### Step 1: Center the Data

Subtract the mean of each feature so the data is centered around the origin.

\[
X_{centered} = X - \mu\] where \(\mu = \frac{1}{n} \sum_{i=1}^{n} X_i\)

### Step 2: Compute the Covariance Matrix

The covariance matrix captures how features vary with one another.

\[
\Sigma = \frac{1}{n-1} X_{centered}^T X_{centered}
\]

Each entry \( \Sigma_{ij} \) represents the covariance between features \( i \) and \( j \).

### Step 3: Eigen Decomposition

Find **eigenvalues** and **eigenvectors** of the covariance matrix:

\[
\Sigma v_i = \lambda_i v_i
\]

- \( v_i \): eigenvector (direction of principal component)  
- \( \lambda_i \): eigenvalue (amount of variance explained by that component)

The eigenvectors form new coordinate axes, and eigenvalues indicate the importance (variance) of each axis.

### Step 4: Sort and Select Principal Components

Sort eigenvectors in descending order of their eigenvalues:

\[
\lambda_1 \geq \lambda_2 \geq \dots \geq \lambda_d
\]

Choose the top \( k \) eigenvectors that explain most of the variance.  
Form the **projection matrix** \( W \in \mathbb{R}^{d \times k} \).

### Step 5: Project the Data

Transform the original data to the new subspace:

\[
Z = X_{centered} W
\]

Here, \( Z \) is the representation of your data in the reduced \( k \)-dimensional space.

## 4. PCA Implementation Steps

1. **Standardize** the dataset (zero mean, unit variance)  
2. **Compute** the covariance matrix  
3. **Perform** eigen decomposition (or SVD)  
4. **Select** top \( k \) components based on variance explained  
5. **Project** data onto these components
