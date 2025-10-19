## What Are Outliers?

Outliers are data points that are significantly different from most of the other observations in a dataset.

They may:

- Have values that are too high or too low compared to the rest,
- Not follow the general trend or pattern in the data,
- Be caused by errors (e.g., data entry, sensor malfunction), or sometimes represent rare but real events (like fraud or system failure).
  
## Why Outliers Matter

Outliers can:

- Distort averages (mean, variance)
- Mislead models (especially linear ones)
- Affect performance if not handled properly
- But sometimes they’re valuable signals — e.g., fraudulent transactions, rare diseases, or system anomalies

## How to Detect Outliers

There are three main ways to detect outliers:

**1. Statistical Methods**
Z-score method:

$$Z = \frac{(x − \mu)}{\sigma}$$


If $|Z| > 3$ → likely an outlier

**2. IQR method (Interquartile Range):**

$$IQR = Q_3 − Q_1$$

Outliers are values $< Q1 - 1.5×IQR$ or $> Q3 + 1.5×IQR$

**3. Visualization**

- Box plots → Show outliers as points beyond whiskers
- Scatter plots → Spot extreme points visually
- Histogram → Identify values far from main distribution

## Rule of Thumb

Don’t remove outliers blindly — always ask:

> “Is this an error, or an important signal?”