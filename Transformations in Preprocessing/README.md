### What Are Transformers in Machine Learning (Preprocessing)?
In the preprocessing context (like in scikit-learn), a transformer is a component that applies a mathematical function or statistical transformation to features in order to make them more suitable for modeling.

Unlike scalers (which adjust values to specific ranges), transformers typically:
- Change the distribution of data (e.g., reduce skewness, approximate normality)
- Stabilize variance
- Improve model assumptions (especially for linear models, regression, statistical tests).

### 1. Function Transformers
A FunctionTransformer is a general-purpose transformer that applies a user-defined function to input features. It is flexible and allows applying mathematical transformations directly.

#### Some common types of function transformers

**1. Log Transformation**

- Formula: $𝑥'= log(𝑥)$ or $𝑥'= log(1+𝑥)$ if $(x ≥ 0)$
- Reduce right skewness, compresses large values.

**2. Square Root Transformation**
- Formula: $x'= \sqrt{x}$
- Works for moderate skewness, stabilizes variance.

**3. Reciprocal Transformation**

- Formula: $x'= \frac{1}{x}$
- Useful for very large values, extreme skewness.

**4. Exponential Transformation**

- Formula: $x'= e^x$
- Stretches out small values (rarely used, risk of blow-up).

### Limitations of Function Transformers

- Require manual selection → no automatic optimization.
- Some transforms only work for positive values (e.g., log, sqrt).
- Harder to interpret transformed features.

### 2. Power Transformers
 A PowerTransformer is a statistical transformation that automatically finds the best exponent $(λ)$ to make data more Gaussian-like and stabilize variance.
It includes two main families: Box-Cox and Yeo-Johnson.

#### Types of power transformers

**1. Box-Cox Transformation**

- Works only for strictly positive data.

- Formula: $x'(\lambda) =
\begin{cases}
\dfrac{x^\lambda - 1}{\lambda}, & \lambda \neq 0 \\
\log(x), & \lambda = 0
\end{cases}$
- Finds λ automatically by maximum likelihood.

**2. Yeo-Johnson Transformation**

- Works for both positive and negative data.
- Formula: $x'(\lambda) =
\begin{cases}
\frac{(x+1)^\lambda - 1}{\lambda}, & x \geq 0, \; \lambda \neq 0 \\
\log(x+1), & x \geq 0, \; \lambda = 0 \\
-\frac{((-x+1)^{(2-\lambda)} - 1)}{2-\lambda}, & x < 0, \; \lambda \neq 2 \\
-\log(-x+1), & x < 0, \; \lambda = 2
\end{cases}$
- Generalization of Box-Cox that allows negatives.

### Limitations of Power Transformers
- Box-Cox → only valid for positive features.
- Interpretability is harder (transformed values don’t have intuitive meaning).
- Assumes transformation toward Gaussian is always helpful → not always true.