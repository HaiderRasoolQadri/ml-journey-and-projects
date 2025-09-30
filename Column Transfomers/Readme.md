# What is a ColumnTransformer?

A ColumnTransformer in scikit-learn is a tool that allows you to apply different preprocessing steps to different columns of your dataset.
For example:
- Numerical: features → scale or normalize
- Categorical features → encode
## Manual Preprocessing
This means you write separate code for each type of column.
Problems with this approach:
- You must manually keep track of which columns go where.
- Easy to make mistakes (like mixing up column order).
- Hard to reuse when you deploy or retrain.
- No automatic prevention of data leakage.
- Code becomes messy when you have many columns.
- ColumnTransformer

## With a ColumnTransformer
You can define all preprocessing steps in one place.
Benefits over manual preprocessing:
- One unified object: All transformations are stored in one place.
- Cleaner code: Easier to read and maintain.
- Safe: Prevents leakage (fit only on training data).
- Pipeline-ready: Can be chained with a model for end-to-end training.
- Automatic alignment: Keeps track of which transformed features came from which columns.