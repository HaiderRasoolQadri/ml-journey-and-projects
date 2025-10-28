## 1. Logistic Regression

Let’s go through the evolution of logistic regression conceptually — starting from the perceptron, seeing why it’s not optimal, then introducing the sigmoid function, and finally arriving at the gradient descent solution that makes logistic regression optimal.

## Step 1: The Perceptron — The Beginning

**Intuition**

The perceptron (Frank Rosenblatt, 1958) is the simplest model for binary classification.

It’s like:

> “Take inputs, weight them, sum them, and fire (output 1) if the result is above a threshold.”

Mathematically:

\[
\hat{y} =
\begin{cases}
1, & \text{if } w^T x + b > 0 \\
0, & \text{otherwise}
\end{cases}
\]

So the activation function is the Heaviside step function:

\[
f(z) =
\begin{cases}
1, & \text{if } wz > 0 \\
0, & \text{otherwise}
\end{cases}
\]

**Perceptron Learning Trick**

We update the weights whenever the perceptron misclassifies a sample:

$$w = w + \eta (y - \hat{y})x$$

where: $\eta$ is the learning rate.

If the prediction was correct, no update is made.
If it was wrong:

- If $y = 0, \hat{y} = 0$, increase $w$ (make it fire)
- $y = 0, \hat{y} = 1$ decrese w

**Why it’s not optimal**

1. Non-differentiable step function → can’t use calculus or gradient methods.
2. Only works if data are linearly separable.
    If your data overlap even slightly, it’ll never converge.
3. The updates are discrete and somewhat arbitrary — not based on minimizing a continuous loss function.

So we need something smoother — a function that acts like a step, but is differentiable.

## Step 2: The Sigmoid Trick
**Intuition**

Let’s replace the hard step with a soft, smooth version — the sigmoid function:

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

It smoothly squashes real numbers into 

- If $𝑧 → +\infty, \sigma{(z)} → 1$
- If $𝑧 → -\infty, \sigma{(z)} → 0$

Now, we can interpret the output as a probability:

$$\hat{y} = P(y = 1 ∣ x) = \sigma(w^Tx)$$

**The “Not Optimal Yet” Solution**

At first, we could still use something like a mean squared error (MSE) loss:

$$L = \frac{1}{2n} \sum(y - \hat{y})^2$$ 

and update with:

$$w = w + \eta (y - \hat{y}) x$$

This is kind of okay because it’s differentiable — but not ideal.

**Why MSE with sigmoid is not optimal**

1. Non-convex loss → can have multiple local minima.
2. Gradient vanishes when sigmoid saturates (at 0 or 1), so learning slows drastically.
3. It doesn’t correspond to a true probabilistic model — it doesn’t model uncertainty correctly.

So we need a loss function that is both convex and probabilistically sound.

## Step 3: Logistic Regression — Gradient Descent on Log Loss

**Intuition**

Let’s think in probabilities:

We want to model:

\[
P(y|x) = \begin{cases}
\hat{y} = \sigma(w^Tx), & if y = 1 \\
1 - \sigma(w^Tx), & if y = 0
\end{cases}
\]

**Define the Loss Function (Log-Likelihood)**

To find the best weights, we maximize the likelihood of observing the data.
Equivalently, we minimize the negative log-likelihood (the log loss):

$$L(w) = -\frac{1}{n} \sum_{i = 1}^{n} [y_i log (\hat{y}_i) + (1 - y_i) log (1 - \hat{y}_i)]$$

This loss is:

- Convex (so only one minimum)
- Differentiable (so we can use calculus)
- Probabilistically sound

**Gradient Descent Solution**

Compute the gradient:

\[
\nabla_w L = -\frac{1}{n} X^T (y - \hat{y})
\]

Then update:

\[
w = w - \eta \nabla_w L = w + \eta \frac{1}{n} X^T (y - \hat{y})
\]

**Why This is Optimal**

- The loss is convex → gradient descent finds a global minimum.
- The sigmoid ensures differentiability.
- The log-likelihood ensures statistical optimality — you’re finding the maximum likelihood estimate for 𝑤.
- The gradient gives smooth, well-scaled updates.

## 2. Softmax Regression (Multiclass Logistic Regression)
**The problem it solves**

Standard (sigmoid) logistic regression can only handle two classes (e.g., spam / not spam).
What if we have more than two categories, like:

- Digit classification (0–9)
- Sentiment (positive / neutral / negative)
- Types of animals (dog / cat / horse)

That’s where softmax regression (also called multinomial logistic regression) comes in.

**The idea**

We assign a separate weight vector $𝑤_𝑘$ to each class 𝑘.
For an input 𝑥, we compute a score for each class:

$$z_k = w_k^Tx$$

Then, instead of a sigmoid, we use the softmax function to convert these scores into probabilities:

$$P(y = k ∣ x) = \frac{e^z_k}{\sum_{j=1}^{K} e^z_j}$$

Each class 𝑘 gets a probability between 0 and 1, and all probabilities sum to 1:

$$\sum{k=1}^{K} P( y = k ∣ x) = 1$$

**Training (Loss Function)**

We use the cross-entropy loss across all classes:

\[
L(W) = -\frac{1}{n} \sum_{i=1}^{n} 
\sum_{k=1}^{K} y_{ik} \log P(y_i = k)
\]

where $y_{ij}$ is a one-hot encoded label (1 if sample i belongs to class 𝑘, else 0).

## 3. Polynomial Logistic Regression

**The problem it solves**

Both the perceptron and logistic regression use linear decision boundaries:

$$w^T x + b = 0$$
This means they can only separate data with straight lines (or planes).

But many real-world datasets are nonlinear — for example, circular or spiral patterns can’t be split by a straight line.

**The idea**

We transform the original input features into polynomial features — combinations of powers and interactions — so that logistic regression can form a nonlinear boundary in the original space.
