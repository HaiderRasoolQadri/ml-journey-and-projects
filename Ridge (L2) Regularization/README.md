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

## 2. L2 Regularization (Ridge Regression)

- Adds the square of the weights as a penalty term.

$$Loss = MSE + \lambda \sum_{i=1}^{n} (w_i)^2$$

    Where:
- $\lambda$ = regularization strength (controls penalty amount)
- $w_i$ = model parameters (weights)

### Pros:

- Prevents large coefficients → reduces model variance.
- Works well when most features are useful.
- Helps with multicollinearity by distributing weights more evenly.

### Cons:

- Does not perform feature selection — weights shrink but don't become exactly zero.
- May be less interpretable than L1.