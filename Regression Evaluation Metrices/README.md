## Regression Evaluation Metrics
Regression evaluation metrics help us measure how well a regression model predicts continuous values. Each metric captures different aspects of error, so which one you use depends on the context of your problem.

## Common Regression Evaluation Metrics
### 1. Mean Absolute Error (MAE)

Formula:

$$𝑀𝐴𝐸 = \frac{1}{n}\sum_{i = 1}^{n} |y_i - \hat{y_i}|$$


When to use:
- When you want a simple, interpretable measure of average error.
- Works well if all errors should be treated equally (no heavy penalty for large errors).

Limitations:
- Doesn’t penalize large errors strongly.
- Not differentiable at 0 (minor issue for optimization).

### 2. Mean Squared Error (MSE)

Formula:
$$𝑀S𝐸 = \frac{1}{n}\sum_{i = 1}^{n} (y_i - \hat{y_i})^2$$

When to use:
- When you want to penalize large errors more heavily.
- Commonly used in optimization because it’s differentiable.

Limitations:
- Sensitive to outliers (squaring exaggerates their effect).
- Not as interpretable in the original unit of the data.

### 3. Root Mean Squared Error (RMSE)

Formula:

$$R𝑀S𝐸 = \sqrt{MSE}$$


When to use:
- Same as MSE, but makes results interpretable in the same unit as the target variable.
- Useful when you want to measure how far off predictions are, in original scale.

Limitations:
- Still highly sensitive to outliers.

### 4. R-squared (Coefficient of Determination)

Formula:
$$R^2 = 1 - \frac{\sum(y_i - \hat{y_i})^2}{\sum(y_i - \bar{y})^2}$$

When to use:
- To measure how much variance in the target is explained by the model.
- Useful for comparing models.

Limitations:
- Doesn’t directly tell you about prediction accuracy.
- Can be misleading if data is non-linear.
- Adding more features can artificially inflate $𝑅^2$.

### 5. Adjusted R-squared

Formula:
$$R_{adj}^{2} = 1 - (1 - R^2)\frac{n - 1}{n - p - 1}$$

where,

n = number of samples, 

p = number of predictors.

When to use:
- When comparing models with different numbers of features.

Limitations:
- Still doesn’t measure error in units of the target.
- Can be negative if model is worse than baseline.