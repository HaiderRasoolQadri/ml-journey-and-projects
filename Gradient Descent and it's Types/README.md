## What is Gradient Descent?

Gradient Descent is an optimization algorithm used to minimize a loss (or cost) function in machine learning and deep learning models.

It works by iteratively adjusting parameters (weights) in the direction that reduces the loss most quickly — that is, opposite to the gradient of the loss function.

### Why Do We Need Gradient Descent?

When training machine learning models (like linear regression, neural networks, etc.), we want to find the best parameters (weights, biases) that make the model’s predictions as accurate as possible.

Mathematically, this means minimizing the loss function, for example:

$$J(\theta) = \frac{1}{n} \sum_{i=1}^{n}(y_i - \hat{y_i})^2$$


But for complex models, the loss function $J(θ)$ may not have a simple formula whose minimum can be solved analytically (especially in neural networks).

Hence, Gradient Descent is used to find the minimum numerically.

### How Gradient Descent Works (Intuition)

1. Start with random parameter values (weights).

2. Compute the gradient (slope) of the loss function w.r.t. parameters.

3. Update the parameters by moving them opposite to the direction of the gradient.

**Update Rule:**

$$ \theta := \theta − \alpha . \nabla_{\theta}J(\theta)$$

where:
- $\theta$ = model parameters
- $\alpha$ = learning rate
- $J(\theta)$ = gradient (vector of partial derivatives)

### Why Gradient Descent is Famous in ML

- Scalable: Works even with millions of parameters (deep learning).
- Simple yet powerful: Easy to implement and mathematically elegant.
- Flexible: Can optimize almost any differentiable function.
- Foundation of deep learning: Used in all neural network training.

### Limitations of Gradient Descent
**1. Choosing the Right Learning Rate (α)**

- The learning rate (α) controls how big a step we take in each iteration.
- If α is too small, convergence is very slow.
- If α is too large, the algorithm can overshoot the minimum or even diverge.

**2. Getting Stuck in Local Minima or Saddle Points**

- For non-convex functions (like neural networks), the cost surface can have multiple minima and flat saddle regions.
- Gradient Descent can:

    - Get stuck in a local minimum (not the best solution).
    - Stop in a saddle point (where gradient ≈ 0 but not a minimum).

**3. Feature Scaling Sensitivity**

- Gradient Descent works best when all features have similar ranges.
- If one feature has a much larger scale than others, the gradient in that direction will dominate, leading to inefficient updates.

**4. Non-Differentiable Functions**

- Gradient Descent relies on computing derivatives.
- If the cost function is not differentiable or has discontinuous points, it cannot be optimized directly using standard gradient descent.

## Types of Gradient Descent
### 1. Batch Gradient Descent (BGD)

**Batch Gradient Descent** uses the entire training dataset to compute the gradient of the cost function for each iteration.

So, one update = one pass over the entire dataset.

$$ \theta := \theta − \alpha . \frac{1}{n} \sum_{i=1}^{n} \nabla_{\theta}J_i(\theta)$$

For linear regression with MSE:

$$\theta := \theta − \alpha . \frac{2}{n} \sum_{i=1}^{n}(y_i - \hat{y_i}) x_i$$

**Working:**

1. Compute predictions for all training samples.
2. Compute the average gradient over the whole dataset.
3. Update all parameters simultaneously.

This ensures a smooth and stable path toward the minimum.

**Advantages:**

- Converges smoothly to the global minimum (for convex functions).
- More stable updates because it uses the full dataset.
- Works well when dataset size is small or moderate.

**Disadvantages:**

- Very slow for large datasets (needs to process the entire dataset before each update).
- High memory requirement — must load the full dataset into memory.
- Cannot be used for online learning (streaming data).

### 2. Stochastic Gradient Descent (SGD)
**SGD** updates parameters for each training example, one at a time, rather than waiting for the full dataset.

So each training sample causes one weight update.

$$ \theta := \theta − \alpha . \nabla_{\theta}J_i(\theta)$$

For linear regression with MSE:

$$\theta := \theta − \alpha . (y_i - \hat{y_i}) x_i$$

**Working:**

1. Randomly shuffle training data.

2. For each sample $(x_i, y_i)$
    - Compute prediction.
    - Compute gradient based on that one example.
    - Update parameters immediately.

**Advantages:**

- Very fast updates → can handle very large datasets.
- Online learning: Can learn continuously as data arrives.
- Can escape local minima due to noisy updates (good for deep networks).

**Disadvantages:**

- Updates are noisy, causing cost function to fluctuate instead of smoothly decreasing.
- May not converge exactly to the minimum (but close enough in practice).
- Needs tuning of learning rate carefully to avoid instability.

## 3. Mini-Batch Gradient Descent (MBGD)

Mini-Batch Gradient Descent combines the best of both worlds:
It splits the dataset into small batches (e.g., 32, 64, 128 examples), and performs one update per batch.

$$ \theta := \theta − \alpha . \frac{1}{b} \sum_{i=1}^{b} \nabla_{\theta}J_i(\theta)$$

where;

b = batch size (e.g 32, 64, 128, etc.)

**Working:**

1. Divide dataset into small batches of size b.

2. For each batch:
    - Compute the gradient of that batch.
    - Update parameters.
3. Repeat until convergence.

This approach provides computational efficiency and stable convergence.

**Advantages:**

- Faster than BGD, more stable than SGD.
- Efficient GPU use → vectorized batch operations.
- Less noisy convergence than pure SGD.
- Often gives the best practical performance for deep learning.

**Disadvantages:**

- Choosing batch size affects performance (too small → noisy; too large → slow).
- Still may get stuck in local minima for non-convex functions.