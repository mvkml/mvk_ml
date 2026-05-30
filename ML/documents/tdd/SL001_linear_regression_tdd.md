# TDD — SL001: Linear Regression

**Document Type:** Technical Design Document
**Topic ID:** SL001
**Algorithm:** Linear Regression
**Owner:** Architect Agent
**Created:** 2026-05-30
**Status:** In Progress

---

## 1. Algorithm Overview

Linear Regression fits a straight line (or hyperplane in multiple dimensions) through data points such that the sum of squared differences between actual and predicted values is minimized. It is a parametric, deterministic algorithm — the same input always gives the same output.

---

## 2. Mathematical Foundation

### Simple Linear Regression (1 feature)
```
ŷ = w₀ + w₁·x

Where:
  ŷ  = predicted value
  w₀ = intercept (bias)
  w₁ = coefficient (slope / weight)
  x  = input feature
```

### Multiple Linear Regression (n features)
```
ŷ = w₀ + w₁·x₁ + w₂·x₂ + ... + wₙ·xₙ

In matrix form:
  ŷ = X · w

Where:
  X = feature matrix (m samples × n features, with 1 column prepended for bias)
  w = weight vector (n+1 × 1)
```

### Cost Function — Mean Squared Error (MSE)
```
MSE = (1/m) · Σ(ŷᵢ - yᵢ)²

Where:
  m  = number of training samples
  yᵢ = actual value
  ŷᵢ = predicted value
```

### Ordinary Least Squares (OLS) — Closed-form Solution
```
w = (XᵀX)⁻¹ · Xᵀ · y

This directly computes the optimal weights in one step.
sklearn's LinearRegression uses this by default.
```

### Gradient Descent (iterative alternative)
```
w := w - α · (1/m) · Xᵀ · (Xw - y)

Where:
  α = learning rate
  Xᵀ(Xw - y) = gradient of cost w.r.t. weights

Used when dataset is too large for OLS (OLS is O(n³) to invert XᵀX).
```

---

## 3. Step-by-Step Algorithm Logic

```
1. Collect training data: (X_train, y_train)
2. Optionally scale features (StandardScaler)
3. Prepend bias column of 1s to X
4. Compute weights via OLS: w = (XᵀX)⁻¹ Xᵀy
5. For prediction: ŷ = X_test · w
6. Evaluate: compute R², MAE, MSE, RMSE on test set
```

---

## 4. Hyperparameters (sklearn LinearRegression)

| Parameter | Default | Description | When to Change |
|---|---|---|---|
| `fit_intercept` | `True` | Whether to calculate intercept w₀ | Set False only if data is already centered |
| `copy_X` | `True` | Copy X before fitting | Set False to save memory on large datasets |
| `n_jobs` | `None` | Parallelism for large X | Set to -1 for multi-core on large data |
| `positive` | `False` | Force all coefficients ≥ 0 | Use if domain requires non-negative coefficients |

> Note: sklearn LinearRegression has no regularization. For regularization, use Ridge (L2) or Lasso (L1) — covered in SL009.

---

## 5. Evaluation Metrics

| Metric | Formula | Interpretation | sklearn function |
|---|---|---|---|
| **R² (R-squared)** | `1 - SS_res/SS_tot` | % variance explained (1.0 = perfect) | `r2_score(y, ŷ)` |
| **MAE** | `mean(|y - ŷ|)` | Average absolute error in original units | `mean_absolute_error(y, ŷ)` |
| **MSE** | `mean((y - ŷ)²)` | Average squared error (penalizes outliers more) | `mean_squared_error(y, ŷ)` |
| **RMSE** | `sqrt(MSE)` | Same unit as target, easier to interpret | `np.sqrt(mean_squared_error(y, ŷ))` |

---

## 6. Python Implementation Design

```python
# === SL001: Linear Regression ===
# Dataset: California Housing (sklearn built-in)

# --- 1. Imports ---
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_absolute_error, mean_squared_error

# --- 2. Load Data ---
data = fetch_california_housing(as_frame=True)
df = data.frame  # 20640 rows × 9 columns (8 features + 1 target)

# --- 3. EDA ---
# df.shape, df.describe(), df.isnull().sum()
# Correlation heatmap
# Distribution of target (MedHouseVal)

# --- 4. Preprocessing ---
X = df.drop(columns=['MedHouseVal'])
y = df['MedHouseVal']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled  = scaler.transform(X_test)

# --- 5. Train ---
model = LinearRegression()
model.fit(X_train_scaled, y_train)

# --- 6. Evaluate ---
y_pred = model.predict(X_test_scaled)
r2   = r2_score(y_test, y_pred)
mae  = mean_absolute_error(y_test, y_pred)
mse  = mean_squared_error(y_test, y_pred)
rmse = np.sqrt(mse)

# --- 7. Visualize ---
# Actual vs Predicted scatter plot
# Residuals plot (residuals vs predicted)
# Coefficients bar chart
```

---

## 7. Strengths and Weaknesses

| Strengths | Weaknesses |
|---|---|
| Simple and fast to train | Assumes linear relationship |
| Highly interpretable (coefficients) | Sensitive to outliers |
| Works well when relationship is truly linear | Fails on non-linear patterns |
| No hyperparameter tuning needed (basic form) | Requires feature scaling for fair coefficients |
| Provides statistical significance of features | Affected by multicollinearity |
| Good baseline model | No regularization → can overfit with many features |

---

## 8. Residual Analysis Design

```
Residual = y_actual - y_predicted

Good model residuals should:
  - Be randomly scattered around zero
  - Show no pattern (no fan shape, no curve)
  - Follow a roughly normal distribution

Plots to create:
  1. Residuals vs Predicted values  → checks homoscedasticity
  2. Histogram of residuals         → checks normality
  3. Q-Q plot of residuals          → confirms normality
```

---

## 9. Folder Structure

```
ML/
└── SL/
    └── SL001/
        └── linear_regression/
            └── linear_regression.ipynb   ← main implementation notebook
```

---

## 10. Technical Constraints

| Constraint | Detail |
|---|---|
| Dataset size | California Housing: 20,640 rows × 8 features — well within sklearn memory |
| OLS complexity | O(n²p + p³) where p = features — fast for this dataset |
| Scaling required | StandardScaler needed so all coefficients are on comparable scale |
| Python version | 3.11+ |
| sklearn version | 1.3+ |

---

*Previous document: [FDD — SL001](../fdd/SL001_linear_regression_fdd.md)*
*Next document: [Interview — SL001](../interview/SL001_linear_regression_interview.md)*
