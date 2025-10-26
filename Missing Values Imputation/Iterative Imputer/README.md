## What is Iterative Imputer?

Iterative Imputer (`from sklearn.impute.IterativeImputer`) fills in missing values by modeling each feature as a function of the others — using a regression-like approach.

You can think of it as "machine learning–based imputation".

## Step-by-Step Intuition

1. Choose one feature with missing values, say Age.

   - Treat Age as the target (y)
   - Treat all other remaining features as predictors (X).

2. Train a regression model to predict Age from the other columns — using rows where Age is known.

3. Use that model to predict the missing Age values.

4. Move to the next feature with missing values (say, Salary), and repeat the process:

   - Now treat Salary as the target, and the other features (including the now-imputed Age) as predictors.

5. Repeat this process iteratively until the imputations stabilize (i.e., they stop changing much between rounds).

That’s why it’s called Iterative Imputer — because it keeps looping through columns until convergence.

## Why it’s Powerful

- It learns relationships between variables (unlike Mean or KNN).
- It can handle complex correlations between features.
- It uses predictive modeling for more accurate imputations.

## In simple terms:

Iterative Imputer is like having a “mini machine learning model” for each column — each model predicts the missing values of that column using the other columns as inputs.
It refines these predictions iteratively until they make sense together.