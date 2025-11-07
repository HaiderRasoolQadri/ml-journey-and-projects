# What Are Outliers?

---

**Outliers** are data points that differ significantly from the majority of observations in a dataset.

They may:
- Have unusually **high or low values** compared to most data.
- **Break the general trend** or pattern.
- Arise from **errors** (e.g., data entry mistakes, sensor malfunctions) or **rare but valid events** (e.g., fraud, system failure, extreme weather).

##  Why Outliers Matter

Outliers can:
- **Distort summary statistics** (mean, variance, correlations)
- **Mislead predictive models**, especially linear models
- **Impact feature scaling** (e.g., in normalization or standardization)
- **Reveal valuable information**, like:
  - Fraudulent transactions   
  - Rare diseases 
  - Equipment failures 

##  How to Detect Outliers

### 1. Statistical (Z-score) Method

Formula:

\[
Z = \frac{(x - \mu)}{\sigma}
\]

If \(|Z| > 3\), the point is likely an outlier.

**When to use:**
- Data is approximately **normally distributed**
- You want a **quick, numeric** method

**Handling:**
- Replace extreme values (capping) with limits (e.g., Z = 3 or -3)
- Remove only if confirmed to be **erroneous** or **irrelevant**

### 2. IQR (Interquartile Range) Method

Formula:

\[
IQR = Q_3 - Q_1
\]

Outliers are:

\[
x < Q_1 - 1.5 \times IQR \quad \text{or} \quad x > Q_3 + 1.5 \times IQR
\]

**When to use:**
- Data is **skewed** or **non-normal**
- Works well for **small to medium** datasets

**Handling:**
- Cap at lower and upper limits (Winsorization)
- Remove only if clearly invalid

### 3. Visualization-Based Methods

- **Box plots** → Show outliers as dots beyond whiskers  
- **Scatter plots** → Reveal isolated or trend-breaking points  
- **Histograms** → Identify values far from the main distribution  

**When to use:**
- For **exploratory data analysis (EDA)**
- To **understand the context** of extreme values

**Handling:**
- Decide based on **domain knowledge**
- Visual cues help confirm if outliers are genuine or errors

##  Rule of Thumb

 > **Don’t remove outliers blindly.**  
 
 Always ask:

1.  Is this an **error** or a **real phenomenon**?  
2.  Will removing it **improve or distort** the analysis?  
3.  Can it be **handled** through transformation or robust modeling?

