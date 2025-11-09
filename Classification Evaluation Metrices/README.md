# Evaluation Metrics for Classification Models
---
## Introduction
After training a classification model, it's not enough to just look at **accuracy** — sometimes, a model with high accuracy can still perform *poorly* in real-world scenarios.

For example:
- An email spam filter that misses spam messages.
- A medical test that fails to detect a rare disease.

To properly evaluate models, we use **evaluation metrics** that go beyond accuracy.

## 1. Accuracy Score
**Accuracy** measures the proportion of correctly predicted instances among all predictions.

\[
\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}
\]

Where:
- **TP (True Positive)**: Correctly predicted positive cases  
- **TN (True Negative)**: Correctly predicted negative cases  
- **FP (False Positive)**: Incorrectly predicted positive cases  
- **FN (False Negative)**: Incorrectly predicted negative cases  

 **Good when:** classes are balanced  
**Misleading when:** dataset is imbalanced (e.g., rare disease detection)

##  2. Confusion Matrix
A **confusion matrix** shows how many instances were correctly or incorrectly classified.

|                | Predicted: Positive | Predicted: Negative |
|----------------|---------------------|---------------------|
| **Actual: Positive** | True Positive (TP) | False Negative (FN) |
| **Actual: Negative** | False Positive (FP) | True Negative (TN) |

**Example: Email Classifier**
|                | Predicted: Spam | Predicted: Not Spam |
|----------------|-----------------|----------------------|
| **Actual: Spam** | TP = 90 | FN = 10 |
| **Actual: Not Spam** | FP = 20 | TN = 880 |

Accuracy = (90 + 880) / 1000 = **0.97**

Even though accuracy is high, **20 false positives** mean 20 important emails go to spam — bad user experience!

## 3. Type I and Type II Errors

| Error Type | What It Means | Example (Email Classifier) | Example (Rare Disease Prediction) |
|-------------|----------------|----------------------------|------------------------------------|
| **Type I (False Positive)** | Model predicts Positive but it’s actually Negative | Marks a normal email as spam | Predicts disease when person is healthy |
| **Type II (False Negative)** | Model predicts Negative but it’s actually Positive | Misses a spam email | Misses a disease patient |

###  Why they matter:
- **Email Example:** Type I (false positive) is more harmful — user misses important mail.  
- **Medical Example:** Type II (false negative) is more harmful — patient doesn’t get treatment.

**Choosing the best model depends on which error matters more in your problem.**

## 4. Precision, Recall, and F1 Score

| Metric | Formula | Measures | When Important |
|---------|----------|-----------|----------------|
| **Precision** | TP / (TP + FP) | How many predicted positives are correct | When false positives are costly (spam filter) |
| **Recall (Sensitivity)** | TP / (TP + FN) | How many actual positives were found | When false negatives are costly (medical test) |
| **F1 Score** | 2 × (Precision × Recall) / (Precision + Recall) | Balance between precision & recall | When both errors matter |

### Intuition:
- **Precision:** Of all predicted spam emails, how many were actually spam?  
- **Recall:** Of all real spam emails, how many did we catch?  
- **F1:** Overall balance between both.

## 5. ROC and AUC–ROC Curve

### ROC (Receiver Operating Characteristic) Curve
Plots the relationship between:
- **True Positive Rate (Recall)**  
- **False Positive Rate (FPR = FP / (FP + TN))**

Each point on the ROC curve represents a threshold for classifying probabilities as positive or negative.

### AUC (Area Under the Curve)
Measures how well the model can distinguish between classes:
- **AUC = 1.0:** Perfect model  
- **AUC = 0.5:** Random guessing  

###  Example: Spam Detection
- AUC close to 1.0 → Model easily separates spam from non-spam  
- AUC near 0.5 → Model performs like random guessing  

##  Summary

| Metric | Description | When to Focus |
|---------|--------------|----------------|
| Accuracy | Overall correctness | Balanced data |
| Precision | Correct positive predictions | Minimize false positives |
| Recall | Correctly detected positives | Minimize false negatives |
| F1 Score | Balance between precision & recall | Mixed importance |
| ROC–AUC | Ability to separate classes | Probability-based models |

**Takeaway:**  
Different problems prioritize different metrics.  
- For spam filters → prioritize **Precision**  
- For disease detection → prioritize **Recall**