## Hyperparameter Tuning in Machine Learning
---
##  Introduction
When building machine learning models, we have two types of parameters:

1. **Model Parameters** — Learned automatically from data during training (e.g., weights in Linear Regression).
2. **Hyperparameters** — Set *before* training; they control how the model learns (e.g., number of trees, learning rate, regularization strength).

Choosing the right hyperparameters can **greatly improve model performance**.  
This process is called **Hyperparameter Tuning**.

## Why is Hyperparameter Tuning Important?
- Prevents **underfitting** (model too simple) and **overfitting** (model too complex).  
- Helps find the **optimal bias-variance tradeoff**.  
- Improves **generalization** — performance on unseen data.

## Types of Hyperparameter Tuning Techniques

### 1. Manual Search
You pick combinations of parameters by intuition or experience and test them manually.

- Simple  
- Time-consuming, subjective, not scalable

### 2. Grid Search
Tries **all possible combinations** of hyperparameter values from a predefined grid.

- Exhaustive  
- Computationally expensive for large grids

### 3. Random Search
Selects **random combinations** of hyperparameters instead of testing all possible ones.

-  Faster than Grid Search  
-  Often finds good results quickly  
- Might miss the absolute best combination

### 4. Bayesian Optimization (Advanced)
Uses previous evaluations to model the performance landscape and choose the next best set of parameters intelligently.

-  Efficient  
-  More complex to implement (using libraries like Optuna, Hyperopt, or Scikit-Optimize)

## Comparison of Methods

| Method | Search Space | Speed | Ease of Use | Accuracy |
|--------|---------------|--------|-------------|-----------|
| Manual Search | Limited | Slow | Easy | Low |
| Grid Search | Exhaustive | Slow | Easy | High |
| Random Search | Random Samples | Fast | Easy | Medium–High |
| Bayesian Optimization | Smart Sampling | Fast | Medium | Very High |
