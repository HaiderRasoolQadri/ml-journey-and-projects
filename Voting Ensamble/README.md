## 1. What Are Ensemble Techniques?

Ensemble techniques in machine learning are methods that combine multiple models (often called “weak learners”) to create a stronger, more accurate model.

The main idea:

> “A group of models working together performs better than any single model alone.”

This works because different models often make different errors — by combining them, we can cancel out individual weaknesses and improve overall performance.

## 2. Types of Ensemble Techniques

There are three main families:

| Type | Examples | Core Idea |
|------|-----------|-----------|
| **1. Bagging (Bootstrap Aggregating)** | Random Forest | Train models in parallel on different random subsets of data and average their predictions. |
| **2. Boosting** | AdaBoost, XGBoost, LightGBM | Train models sequentially, each focusing on fixing the errors of the previous one. |
| **3. Voting / Stacking** | Hard Voting, Soft Voting, Stacking | Combine predictions from multiple different models to make a final decision. |

## 3.1 What Is Voting Ensemble?

The Voting Ensemble method is the simplest and most intuitive ensemble technique.

It combines predictions from different machine learning algorithms (like Logistic Regression, Decision Tree, SVM, etc.) and makes a final prediction based on majority votes (for classification) or average(for regression).

### 3.1.1 Types of Voting:

**A. Hard Voting**

- Each model votes for a class label.
- The final prediction is the class with the majority votes.

 **B. Soft Voting**

- Each model outputs probabilities for each class.
- We take the average probability across all models and choose the class with the highest average probability.

**C. Weighted Voting**

Weighted Voting is an extension of the Voting Ensemble method where each model’s vote is not equal — instead, models are given different weights based on their performance or importance.

So instead of simple majority or equal averaging, the final prediction gives more influence to better models.

Think of a team decision:

You have three experts.

- One is very experienced, another is average, and the third is new.
- Instead of counting all votes equally, you give the experienced expert’s opinion more weight.
- Same idea applies here — if one model is more accurate, it should contribute more to the final prediction.

### 3.1.2 Working Intuition

Imagine you ask 5 doctors for a diagnosis.
Each might not be perfect, but if most say “flu,” it’s probably the flu.

Similarly:

- Each ML model captures different patterns in the data.
- Voting combines their “opinions” to get a more reliable final decision.
- It reduces variance and improves generalization on unseen data.