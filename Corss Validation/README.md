## Cross Validation in Machine Learning
---
##  What is Cross-Validation?
**Cross-validation (CV)** is a model validation technique used to **assess how the results of a statistical analysis will generalize** to an independent dataset.  
It helps in detecting **overfitting** and ensures the model performs consistently across different subsets of data.

Instead of using just one train-test split, CV divides the dataset into **multiple subsets (folds)** and tests the model multiple times.

##  Types of Cross-Validation

### 1. Hold-Out Method
- Simplest form of validation.  
- Data is split once into:
  - Training set (e.g. 80%)
  - Testing set (e.g. 20%)
- Model is trained on training data and tested once on testing data.  

### 2. K-Fold Cross Validation
- Data is split into **K equal parts (folds)**.
- The model is trained **K times**:
  - Each time, one fold is used as the **validation set**, and the remaining K−1 folds are used as **training data**.
- The final performance metric is the **average** of all K runs.

 **Advantages:**
- Reduces variance in performance estimates.
- Uses data more efficiently than a single hold-out split.

### 3. Stratified K-Fold Cross Validation
- Similar to K-Fold, but it ensures **each fold has the same class proportion** (useful for classification tasks with imbalanced data).
- Example: If your dataset has 70% class A and 30% class B, each fold will preserve that ratio.

### 4. Leave-One-Out Cross Validation (LOOCV)
- Special case of K-Fold where K = number of samples.
- Each data point becomes a **test set** once, and the rest form the training set.
- Extremely accurate but **computationally expensive**.

### 5. Repeated K-Fold Cross Validation
- Repeats K-Fold CV multiple times with different random splits.
- Provides an even more reliable estimate but increases computational time.

##  When to Use Which?

| Type | Use Case |
|------|-----------|
| Hold-Out | Quick testing or large datasets |
| K-Fold | General-purpose validation |
| Stratified K-Fold | Classification with imbalanced classes |
| LOOCV | Small datasets |
| Time Series CV | Time-dependent data |
