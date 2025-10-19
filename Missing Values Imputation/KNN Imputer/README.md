## What is KNN Imputer?

KNN Imputer (K-Nearest Neighbors Imputer) is a method that fills in missing values by using the values from similar rows (neighbors) in your dataset.

Step-by-step intuition

**1. Find the missing value**
Let’s say we’re missing a value in column “Weight”.

**2. Find similar rows (neighbors)**
For the row with the missing value, the algorithm computes distances to other rows (e.g., using Euclidean distance) based on available features.

**3.  Pick the k nearest neighbors**
Example: k=3 → use the 3 most similar rows.

**4. Impute the missing value**
Take the average (for numeric) or most frequent (for categorical) value among those neighbors, and use it to fill in the gap.

## When to Use KNN Imputer

Good for:

- When missing data is not random (depends on other features)
- When features are numerical and correlated
- When you have moderate dataset size (not huge)

Not ideal when:

- Dataset is very large → distance computation is expensive.
- Data has many categorical features → KNN works best for numeric data.
- There are too many missing values → hard to find reliable neighbors.