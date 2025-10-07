### Multiple Linear Regression

Multiple Linear Regression is a statistical technique used to model the relationship between one dependent variable 𝑦 and two or more independent variables $x_1, x_2 ,..., x_f$. 
It is the natural extension of simple linear regression (which only uses one predictor).

### Model Equation
$$y_i = \beta_o + \beta_1x_{i1} + \beta_2x_{i2} +...+ \beta_px_{ip}$$

where:

$y_i$= dependent variable (target) for observation 𝑖

$x_{ip} = p^{th}$ predictor (independent variable) for observation 𝑖

$\beta_o$ = intercept (value of y when all $𝑥_𝑗=0$)

$\beta_j$ = regression coefficient (slope) for predictor $𝑥_j$

### Matrix Form (compact way to write it)
$$𝑦 = 𝑋\beta$$

where:

y = vector of outputs (𝑛 × 1)

X = design matrix including all predictors (n * (p + 1))

β = vector of coefficients ((p + 1) * 1)

### Example

Predicting house prices (y) based on:
- Size $(𝑥_1)$
- Number of bedrooms $(𝑥_2)$
- Location score $(𝑥_3)$
$$Price = \beta_o + \beta_1(Size) + \beta_2(Bedrooms) + \beta_3(Location)$$

### Key Assumptions

1. Linearity: Relationship between predictors and target is linear.
2. Independence: Observations are independent.
3. No (or little) multicollinearity: Predictors are not highly correlated with each other.