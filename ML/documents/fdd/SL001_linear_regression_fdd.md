# FDD — SL001: Linear Regression

**Document Type:** Functional Design Document
**Topic ID:** SL001
**Algorithm:** Linear Regression
**Owner:** Product Owner Agent
**Created:** 2026-05-30
**Status:** In Progress

---

## 1. Purpose

Linear Regression is a supervised learning algorithm that models the relationship between one or more input features and a continuous numeric output (target). It finds the best-fit straight line (or hyperplane) through the data by minimizing prediction error.

---

## 2. Problem Statement

**Problem:** Given a set of input features (X), predict a continuous numeric target value (y).

**Example:** Given house features (size, bedrooms, location score), predict the house price.

---

## 3. When To Use

| Condition | Use Linear Regression? |
|---|---|
| Target is a continuous number (price, salary, score) | Yes |
| Relationship between features and target is approximately linear | Yes |
| Need an interpretable, explainable model | Yes |
| Need to understand feature impact (coefficients) | Yes |
| Target is a category (Yes/No, Class A/B/C) | No — use Logistic Regression or Decision Tree |
| Relationship is highly non-linear | No — use Tree-based models |
| Data has many outliers with no treatment | Caution — outliers distort the fit |

---

## 4. Real-World Use Cases

| Domain | Use Case | Input Features (X) | Target (y) |
|---|---|---|---|
| Real Estate | House price prediction | Size, rooms, location score | Price (₹ or $) |
| HR / Salary | Salary estimation | Years of experience, skills | Salary |
| Retail | Sales forecasting | Ad spend, season, promotions | Revenue |
| Healthcare | Patient risk score | Age, BMI, glucose | Risk score |
| Finance | Stock trend baseline | Volume, past price | Next-day price |
| Education | Student score prediction | Study hours, attendance | Exam score |

---

## 5. Input and Output

| Component | Description |
|---|---|
| **Input (X)** | One or more numeric features (can include encoded categoricals) |
| **Output (y)** | Single continuous numeric value |
| **Model output** | Predicted value `ŷ` for each input row |

**Simple Linear Regression:** One feature → `y = w₀ + w₁·x`

**Multiple Linear Regression:** Multiple features → `y = w₀ + w₁·x₁ + w₂·x₂ + ... + wₙ·xₙ`

---

## 6. Key Assumptions

| # | Assumption | What Happens if Violated |
|---|---|---|
| 1 | **Linearity** — relationship between X and y is linear | Poor fit, biased predictions |
| 2 | **Independence** — observations are independent of each other | Inflated R², unreliable coefficients |
| 3 | **Homoscedasticity** — residuals have constant variance | Heteroscedasticity causes unreliable intervals |
| 4 | **Normality of residuals** — errors follow a normal distribution | Affects statistical tests (p-values) |
| 5 | **No multicollinearity** — features are not highly correlated | Unstable coefficients, hard to interpret |
| 6 | **No significant outliers** | Outliers pull the regression line |

---

## 7. What the Model Learns

- **Coefficients (weights):** How much each feature contributes to the prediction
- **Intercept (bias):** The baseline prediction when all features are zero
- **Best-fit line:** Minimizes the sum of squared errors between actual and predicted values

---

## 8. Acceptance Criteria

| Metric | Minimum Threshold | Notes |
|---|---|---|
| R² (Test Set) | ≥ 0.70 | Explains at least 70% of variance |
| MAE | Meaningful for the domain | Low absolute average error |
| RMSE | Lower than baseline (mean predictor) | Root Mean Squared Error |
| Residual plot | No obvious pattern | Confirms linear assumption |

---

## 9. Out of Scope

- Regularization (Ridge, Lasso) — covered in SL009
- Polynomial features — covered as an extension
- Deep learning regression — covered in DL phase

---

## 10. Dependencies

| Dependency | Purpose |
|---|---|
| `sklearn.linear_model.LinearRegression` | Model implementation |
| `sklearn.datasets.fetch_california_housing` | Dataset |
| `sklearn.model_selection.train_test_split` | Train/test split |
| `sklearn.preprocessing.StandardScaler` | Feature scaling |
| `sklearn.metrics` | R², MAE, MSE evaluation |
| `matplotlib`, `seaborn` | Visualization |

---

*Next document: [TDD — SL001](../tdd/SL001_linear_regression_tdd.md)*
