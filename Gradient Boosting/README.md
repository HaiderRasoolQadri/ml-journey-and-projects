## Gradient Boosting: Intuition and Working (Regression & Classification)

### What is Gradient Boosting?

**Gradient Boosting** is an **ensemble learning technique** that builds a strong predictive model by combining many **weak learners** (usually small decision trees) **sequentially**.

Each new model is trained to **correct the errors** (residuals)made by the previous models. It’s called “gradient boosting” because it uses **gradient descent** to minimize a **loss function**.

### Intuition

1. Start with a simple model that makes rough predictions.  
2. Measure how far the predictions are from the truth (residuals).  
3. Train a new model to predict those residuals.  
4. Add this correction to your overall model (scaled by a learning rate).  
5. Repeat until performance stops improving.

Each new model focuses on the **examples the previous ones got wrong**.

### Algorithm Steps

Given training data \((x_i, y_i)\), \(i = 1, 2, …, N\):

1. **Initialize the model:**
   \[
   F_0(x) = \arg\min_c \sum_i L(y_i, c)
   \]
   (For regression with MSE, \(F_0(x)\) = mean of \(y_i\))

2. **For each iteration \(m = 1, 2, …, M\):**
   - Compute **pseudo-residuals**:
     \[
     r_{im} = -\left[\frac{\partial L(y_i, F(x_i))}{\partial F(x_i)}\right]_{F(x) = F_{m-1}(x)}
     \]
   - Fit a weak learner \(h_m(x)\) to predict \(r_{im}\).
   - Compute the optimal weight:
     \[
     \gamma_m = \arg\min_\gamma \sum_i L(y_i, F_{m-1}(x_i) + \gamma h_m(x_i))
     \]
   - Update the model:
     \[
     F_m(x) = F_{m-1}(x) + \eta \gamma_m h_m(x)
     \]
     where \(\eta\) is the **learning rate**.

### Gradient Boosting for Regression

**Loss Function:** Mean Squared Error  
\[
L(y, F(x)) = \frac{1}{2}(y - F(x))^2
\]

Then:
\[
r_{im} = y_i - F_{m-1}(x_i)
\]

Each new tree is fit to the residuals (actual - predicted).

**Intuition:**  
Keep adding trees that "fix" what’s still wrong.


### Gradient Boosting for Classification

**Loss Function:** Logistic Loss  
\[
L(y, F(x)) = \log(1 + e^{-2yF(x)}), \quad y \in \{-1, +1\}
\]

Then:
\[
r_{im} = \frac{2y_i}{1 + e^{2y_i F_{m-1}(x_i)}}
\]

Each new tree predicts these pseudo-residuals (direction of the loss gradient).  
Final prediction:
\[
p(x) = \frac{1}{1 + e^{-2F_M(x)}}
\]

**Intuition:**  
Each tree helps push predicted probabilities closer to the correct class.

### Summary Table

| Task | Loss Function | Residual / Gradient | Interpretation |
|------|----------------|----------------------|----------------|
| Regression | Mean Squared Error | \(y_i - \hat{y}_i\) | Fit trees to residuals |
| Classification | Logistic Loss | \(\frac{2y_i}{1 + e^{2y_i \hat{F}(x_i)}}\) | Fit trees to pseudo-residuals (loss gradient direction) |

**Gradient Boosting = Gradient Descent + Boosting**
- Uses gradients to minimize a chosen loss function.
- Sequentially adds weak models to correct errors.
- Works for both regression and classification tasks.

