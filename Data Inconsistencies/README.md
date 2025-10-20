### Data consistency in ML means that:

The same data point, when referenced in different places or at different times, has the same meaning and value.

If the same customer, timestamp, label, or measurement is represented differently across datasets, it introduces inconsistency — leading to model confusion, bias, or poor generalization.

### Types of Consistency in ML Data

**1. Schema Consistency**

- The structure of data (columns, data types, naming conventions) should be consistent across datasets.
- Example:
  - Training dataset has column customer_id (integer)
  - Test dataset has CustomerID (string) →  inconsistent

**2. Format Consistency**

- Data should follow the same format or units.

- Example:
  - Dates in YYYY-MM-DD in one file and DD/MM/YYYY in another → inconsistent
  - Temperatures in Celsius vs Fahrenheit →  inconsistent

**3. Value Consistency**

- Identical entities or categories should use the same labels or identifiers.
- Example:
  - “Male”, “M”, and “m” → inconsistent labels for gender
  - Should be standardized to one form (e.g., “Male”)

**4. Temporal Consistency**

  Data should align logically over time.

- Example:
    - A customer’s “signup_date” cannot be after their “last_purchase_date” → inconsistent

**5. Statistical Consistency**

- Distribution of features should remain stable (especially between training and testing data).

- Example:
    - If 80% of training samples are from one region but 50% of test samples are from another, the data is statistically inconsistent (a distribution shift).

### Why Consistency Matters

- Improves model accuracy — reduces noise and bias.
- Ensures generalization — models trained on consistent data perform better on unseen data.
- Simplifies feature engineering — fewer special cases or conversions.
- Enables reliable predictions — especially in production settings.