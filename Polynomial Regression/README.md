### Polynomial Regression

Polynomial regression is a type of regression analysis used when the relationship between the independent variable(s) (input) and the dependent variable (output) is nonlinear — but can be modeled as a polynomial function.

Definition: 

Polynomial regression models the relationship between x and y as an $n^{th}$ degree polynomial:

$$y = \beta_o + \beta_1x + \beta_2x^2 + \beta_3x^3 +...+ \beta_nx^n$$

- y dependent variable (output)
- x independent variable (input)
- $\beta_o, \beta_1, \beta_1,..., \beta_n$ are coefficients

It’s essentially linear regression in disguise — we still fit a linear model, but the features (like $x^2, x^3,...$) are nonlinear transformations of x.

### Why We Need Polynomial Regression

1. Nonlinear Relationships

- When data doesn’t follow a straight-line pattern, polynomial regression can capture curves.
- Example: predicting population growth, temperature changes, or performance vs. experience — which may have a curved trend.

2. Improves Model Flexibility

- Allows the model to fit more complex patterns without resorting to completely different nonlinear methods (like neural networks).

3. Still Easy to Interpret

- Despite modeling nonlinear trends, the model remains linear in parameters, so estimation (e.g., via least squares) is simple.

4. Extends Linear Regression

- You can use the same tools and techniques (like $R^2$, residual analysis) from linear regression.

### Be Careful with the Degree of Polynomial

1. Overfitting

- Happens when the polynomial degree is too high.
- The model becomes too flexible and starts fitting the noise in the data, not just the true pattern.
- It performs very well on training data but poorly on new/unseen data.
- The fitted curve looks too wiggly or unstable.
- Example: Using a 10th-degree polynomial when a simple curve would do.

2. Underfitting

- Happens when the polynomial degree is too low.
- The model is too simple and fails to capture the real relationship in the data.
- It performs poorly on both training and test data.
- The fitted line looks too straight for curved data.
- Example: Using a straight line (degree 1) when the data clearly follows a curve.