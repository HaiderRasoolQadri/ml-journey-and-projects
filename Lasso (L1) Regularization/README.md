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

## 1. L1 Regularization (Lasso Regression)

- Adds the absolute value of the weights as a penalty term.

$$Loss = MSE + \lambda \sum_{i=1}^{n} |w_i|$$

    Where:
- $\lambda$ = regularization strength (controls penalty amount)
- $w_i$ = model parameters (weights)

### Pros:

- Feature selection: It can drive some weights to exactly zero, effectively removing unimportant features.
- Leads to sparse models, which are easier to interpret.

### Cons:

- May behave unstably when features are highly correlated — arbitrarily picks one and discards others.
- Can be less accurate than L2 if all features are useful.