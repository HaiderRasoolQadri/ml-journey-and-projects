## Bagging Ensemble Technique

**Bagging (Bootstrap Aggregating)** is an ensemble learning technique that improves the stability and accuracy of machine learning models by combining predictions from multiple base estimators trained on random subsets of the training data.

It reduces **variance** without increasing **bias**, making it especially effective for **high-variance models** (e.g., decision trees).

### Working Intuition

1. **Bootstrap Sampling (with replacement):**  
   - From the original dataset of size *n*, multiple random samples of size *n* are drawn **with replacement**.  
   - This means some observations may appear multiple times in a sample, while others may not appear at all.

2. **Model Training:**  
   - A base model (e.g., decision tree, SVM, etc.) is trained on each bootstrap sample independently.

3. **Aggregation:**  
   - For **regression**, predictions are averaged across all models.  
   - For **classification**, predictions are combined using **majority voting**.

4. **Goal:**  
   - Reduce model variance and improve generalization by leveraging multiple learners trained on slightly different data distributions.

### Types of Bagging Variants

#### 1. Bagging
- Sampling **with replacement** from the training data.
- Each estimator trains on a bootstrap sample.
- Example: `BaggingClassifier` or `RandomForestClassifier` in scikit-learn.

#### 2. Pasting
- Similar to bagging but samples are drawn **without replacement**.
- Reduces randomness compared to bagging.
- Can be useful when the dataset is small and replacement might cause excessive duplication.

#### 3. Random Subspaces
- Instead of sampling data points, this method samples **features**.
- Each estimator is trained using a **random subset of features**, not all.
- Helps reduce correlation between estimators, particularly in high-dimensional datasets.

#### 4. Random Patches
- A combination of **Random Subspaces** and **Bagging/Pasting**.
- Randomly samples both **data points** and **features**.
- Used in algorithms like **Random Forests** (random subset of features + bootstrap samples of data).

| Variant            | Sampling Method          | Sampling Type     | Typical Use Case                            |
|--------------------|--------------------------|-------------------|---------------------------------------------|
| **Bagging**        | With replacement         | Samples (rows)    | Reducing variance in large datasets         |
| **Pasting**        | Without replacement      | Samples (rows)    | Small datasets                              |
| **Random Subspaces** | With/without replacement | Features (columns) | High-dimensional data (feature reduction)   |
| **Random Patches** | With/without replacement | Samples + Features | Used in Random Forests and hybrid models    |

### Out-of-Bag (OOB) Score

**Out-of-Bag (OOB) samples** are the data points **not included** in a particular bootstrap sample.

#### Key Ideas:
- On average, each bootstrap sample contains about **63%** of the original data (since ~37% are left out).
- The remaining **37% (OOB samples)** can be used as a **validation set** for that specific model.
- By aggregating OOB predictions across all models, we can estimate the model’s performance **without using a separate validation set**.
