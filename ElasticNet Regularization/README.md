## What is Regularization?

Regularization is a technique used to penalize model complexity by adding a regularization term (or penalty) to the loss function.

The goal is to make the model simpler and less sensitive to noise in the training data.

Without regularization, a model (especially a complex one like a deep neural network or a high-degree polynomial regression) may fit the training data too well — capturing noise rather than the true underlying pattern.

## Why We Need Regularization

- Prevent overfitting (model performs well on training data but poorly on test data).
- Encourage simpler models with smaller parameter values.
- Improve generalization performance.
- Handle multicollinearity in linear models.

## Common Regularization Techniques

1. Lasso (L1) Regularization 
2. Ridge (L2) Regularization
3. Elastic Net Regularization.

## 3. Elastic Net Regularization 

- Combines L1 and L2 penalties.

$$Loss = MSE + \lambda_1 \sum_{i=1}^{n} |w_i| + \lambda_2 \sum_{i=1}^{n} (w_i)^2$$

or equivalently (as used in scikit-learn):

$$Loss = MSE + \lambda[ \alpha \sum_{i=1}^{n} |w_i| + (1 - \alpha) \sum_{i=1}^{n} (w_i)^2]$$

    Where:
- $\lambda's$ = regularization strength (controls penalty amount)
- $w_i$ = model parameters (weights)

### Pros:

- Balances feature selection (L1) and weight shrinkage (L2).
- Works better with correlated features — can select groups of related features together.
- More flexible than pure L1 or L2.

### Cons:

- More complex to tune (two hyperparameters: λ and α).
- Slightly higher computational cost.