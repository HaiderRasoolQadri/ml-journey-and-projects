# Boosting and AdaBoost — Explained Step-by-Step

## 1. What is Boosting?

Boosting is an **ensemble learning technique** that combines multiple **weak learners** (models that perform slightly better than random guessing) into a **strong learner** with high accuracy.

Unlike **bagging**, where models are trained **independently and in parallel**, in **boosting**, models are trained **sequentially** — each new model focuses on the mistakes made by the previous ones.

## 2. Boosting — General Methodology

Suppose we have a training dataset:
\[
D = \{(x_1, y_1), (x_2, y_2), ..., (x_N, y_N)\}
\]
and we want to combine \(T\) weak learners.

### Step-by-Step

1. **Initialize weights**  
   Assign each training example an equal weight:
   \[
   w_i = \frac{1}{N}, \quad i = 1, 2, \dots, N
   \]
   These weights determine how much attention each example gets during training.

2. **Iteratively train weak learners**
   For each round \(t = 1, 2, ..., T\):
   - Train a weak learner \(h_t(x)\) using the weighted data.
   - Compute the **error** of this learner:
     \[
     \varepsilon_t = \sum_{i: h_t(x_i) \neq y_i} w_i
     \]
   - The better the learner performs, the smaller the error.

3. **Compute the model’s weight**
   Assign a weight \( \alpha_t \) to the learner based on its accuracy:
   \[
   \alpha_t = \frac{1}{2} \ln\left(\frac{1 - \varepsilon_t}{\varepsilon_t}\right)
   \]
   - If the learner performs well (low error), it gets **higher weight**.
   - If it performs poorly (error > 0.5), it gets **lower or even negative weight**.

4. **Update sample weights**
   Increase weights of misclassified samples and decrease weights of correctly classified ones:
   \[
   w_i \leftarrow w_i \times e^{-\alpha_t y_i h_t(x_i)}
   \]
   Then normalize:
   \[
   w_i = \frac{w_i}{\sum_j w_j}
   \]
   Misclassified samples get **more weight**, so the next learner focuses on them.

5. **Final model**
   Combine all weak learners into a strong one:
   \[
   H(x) = \text{sign}\left( \sum_{t=1}^{T} \alpha_t h_t(x) \right)
   \]

## 3. AdaBoost (Adaptive Boosting)

It **adapts** the weights of training examples based on the performance of previous learners — focusing progressively on harder cases.

### AdaBoost Algorithm (Binary Classification)

| Step | Description |
|------|--------------|
| **1. Initialize weights** | \( w_i^{(1)} = \frac{1}{N} \) for all \(i\). |
| **2. For each iteration \(t = 1, 2, ..., T\):** | |
| → Train weak learner \(h_t(x)\) | using current weights \(w_i^{(t)}\). |
| → Compute weighted error | \( \varepsilon_t = \sum_i w_i^{(t)} [h_t(x_i) \neq y_i] \) |
| → Compute learner weight | \( \alpha_t = \frac{1}{2}\ln\left(\frac{1 - \varepsilon_t}{\varepsilon_t}\right) \) |
| → Update sample weights | \( w_i^{(t+1)} = w_i^{(t)} e^{-\alpha_t y_i h_t(x_i)} \) |
| → Normalize weights | \( w_i^{(t+1)} = \frac{w_i^{(t+1)}}{\sum_j w_j^{(t+1)}} \) |
| **3. Final classifier** | \( H(x) = \text{sign}\left(\sum_{t=1}^{T} \alpha_t h_t(x)\right) \) |

