## What is encoding?

Encoding is the process of converting information from one form (usually human-readable) into another form (usually machine-readable).

In **machine learning (ML)**, encoding means converting raw data (like text, categories, or images) into a numerical format that algorithms can understand, because ML models work with numbers, not words or symbols.

## Types of Encoding in Machine Learning

### 1. Label Encoding
- Assigns a unique number to each category.
  ``` For example Color: Red → 0, Blue → 1, Green → 2```
- Simple
- Adds an unintended order 
  Models may think Green > Blue > Red

### 2. One-Hot Encoding
- Creates binary columns (0/1) for each category.
````
Example:

                                Red   Blue   Green
                                1     0       0
                                0     1       0
                                0     0       1

````
- No false order assumption.
- Increase the dimention of the dataset if there are too many categories.

### 3. Ordinal Encoding
- Use when categories have natural order (like Small < Medium < Large).
  ```For example Small → 0, Medium → 1, Large → 2```
- Keeps order information.

### 4. Frequency/Count Encoding
- Replace categories with their frequency in the dataset.
 Example: If “Dog” appears 50 times, “Cat” 30 times, “Horse” 20 times:
 ```Dog → 50, Cat → 30, Horse → 20```

 There are also many other encoding techniques but those are most common one.
