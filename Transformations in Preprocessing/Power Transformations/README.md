### 2. Power Transformers
 A PowerTransformer is a statistical transformation that automatically finds the best exponent $(λ)$ to make data more Gaussian-like and stabilize variance.
It includes two main families: Box-Cox and Yeo-Johnson.

#### Types of power transformers

**1. Box-Cox Transformation**

- Works only for strictly positive data.

Formula: 

$$x'(\lambda) =
\begin{cases}
\dfrac{x^\lambda - 1}{\lambda}, & \lambda \neq 0 \\
\log(x), & \lambda = 0
\end{cases}$$

- Finds λ automatically by maximum likelihood.

**2. Yeo-Johnson Transformation**

- Works for both positive and negative data.
Formula:

$$x'(\lambda) =
\begin{cases}
\frac{(x+1)^\lambda - 1}{\lambda}, & x \geq 0, \; \lambda \neq 0 \\
\log(x+1), & x \geq 0, \; \lambda = 0 \\
-\frac{((-x+1)^{(2-\lambda)} - 1)}{2-\lambda}, & x < 0, \; \lambda \neq 2 \\
-\log(-x+1), & x < 0, \; \lambda = 2
\end{cases}$$

- Generalization of Box-Cox that allows negatives.

**3. Quantile Transformation**
After either Box–Cox or Yeo–Johnson, the data might be approximately normal — but not perfectly.

The quantile transformation then:
- Maps empirical quantiles to those of a perfect normal (or uniform) distribution.
- Guarantees Gaussian-looking features. 

### Limitations of Power Transformers
- Box-Cox → only valid for positive features.
- Interpretability is harder (transformed values don’t have intuitive meaning).
- Assumes transformation toward Gaussian is always helpful → not always true.
- 