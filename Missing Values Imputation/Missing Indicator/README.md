## What Is a Missing Indicator in Imputation?

A missing indicator is a binary flag (0 or 1) that tells the model whether a particular value in the dataset was originally missing before imputation.

In other words, it keeps track of which values were imputed, so the model can potentially learn patterns in the missingness itself.

## Why Do We Need It?

When you impute missing values (e.g., fill them with mean, median, or most frequent value), you’re replacing missing information with an estimate — but you lose the information that a value was missing in the first place.

Sometimes, the fact that a value was missing carries useful information for the model.

## When to Use Missing Indicators

**Use it when:**

- Missingness itself may carry meaning
- You suspect that "missing" is not random 

**Avoid it when:**

- Missing values are purely random
- Adding extra binary columns makes the model unnecessarily complex