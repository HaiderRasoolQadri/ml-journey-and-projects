### 1. Function Transformers
A FunctionTransformer is a general-purpose transformer that applies a user-defined function to input features. It is flexible and allows applying mathematical transformations directly.

#### Some common types of function transformers

**1. Log Transformation**

Formula: 

$$𝑥'= log(𝑥) or 𝑥'= log(1+𝑥) if (x ≥ 0)$$

- Reduce right skewness, compresses large values.

**2. Square Root Transformation**

Formula: 

$$x'= \sqrt{x}$$

- Works for moderate skewness, stabilizes variance.

**3. Reciprocal Transformation**

Formula: 

$$x'= \frac{1}{x}$$

- Useful for very large values, extreme skewness.

**4. Exponential Transformation**

Formula: 

$$x'= e^x$$

- Stretches out small values (rarely used, risk of blow-up).

### Limitations of Function Transformers

- Require manual selection → no automatic optimization.
- Some transforms only work for positive values (e.g., log, sqrt).
- Harder to interpret transformed features.