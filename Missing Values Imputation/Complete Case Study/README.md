## What is Complete Case Analysis (CCA)?

Complete Case Analysis is a method for handling missing data where you drop all rows (cases) that contain any missing values in the variables being analyzed.

In simple terms:

> If a row has even one NaN → remove it completely from the dataset.

### When CCA is Acceptable / Recommended
1. When missingness is completely at random
   If data are Missing Completely At Random (MCAR)
2. When the proportion of missing data is small
    If only a small portion (say, < 5%) of rows have missing values, then dropping them will not significantly harm the dataset or model performanc
3. When the variables with missing values are not critical
    If missing values are in less important variables (not your predictors or target), or if you plan to exclude those variables anyway, CCA can be used.

### When CCA is NOT Recommended
1. When data are NOT missing completely at random
    If missingness depends on:
    - The variable itself 
   - Another variable

    Then dropping those rows biases your dataset — the remaining data aren’t representative.

    This is called:

   - MAR (Missing At Random)
   - MNAR (Missing Not At Random)

    In such cases, imputation (mean/median/ML-based) is better.
2. When missingness is extensive
    If more than 5–10% of your data is missing across important variables.
3. When the target variable has missing values

### What to Check After Complete Case Analysis (CCA)?

When we apply Complete Case Analysis (CCA) — meaning we remove all rows that contain any missing values — the structure of our dataset can change.
Therefore, it’s essential to check how the data’s characteristics have changed after performing CCA.

#### 1. For Numerical Variables → Check the Distribution

After removing rows, we need to ensure that the shape, mean, and spread of numerical variables remain consistent with the original dataset.

If the missing data were not random, CCA can cause the distributions to shift — for example, you might lose more low-income individuals, raising the average income.

#### 2. For Categorical Variables → Check the Ratios

In categorical data, dropping rows might change the proportion of each category.
If missingness was related to category membership, certain groups may become under- or over-represented after CCA.