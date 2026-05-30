# Interview Q&A — SL001: Linear Regression

**Document Type:** Interview Preparation
**Topic ID:** SL001
**Algorithm:** Linear Regression
**Owner:** Tech Interviewer Agent
**Created:** 2026-05-30
**Status:** In Progress

---

## Core Questions (Must Know)

### Q1. What is Linear Regression?

**Answer:**
Linear Regression is a supervised learning algorithm that models the relationship between input features (X) and a continuous numeric target (y) by fitting a straight line (or hyperplane). The goal is to find the best-fit line that minimizes prediction error.

**Formula:** `ŷ = w₀ + w₁x₁ + w₂x₂ + ... + wₙxₙ`

---

### Q2. How does Linear Regression find the best-fit line?

**Answer:**
It minimizes the **Mean Squared Error (MSE)** — the average of squared differences between actual and predicted values.

Two approaches:
- **Ordinary Least Squares (OLS):** Closed-form solution `w = (XᵀX)⁻¹Xᵀy` — computes exact answer directly
- **Gradient Descent:** Iteratively adjusts weights in the direction that reduces the cost function — used for large datasets where OLS matrix inversion is too expensive

sklearn's `LinearRegression` uses OLS by default.

---

### Q3. What are the assumptions of Linear Regression?

**Answer:** There are 5 key assumptions:

| # | Assumption | Violation Effect |
|---|---|---|
| 1 | **Linearity** — linear relationship between X and y | Biased predictions |
| 2 | **Independence** — observations are independent | Inflated R², false precision |
| 3 | **Homoscedasticity** — constant variance of residuals | Unreliable confidence intervals |
| 4 | **Normality of residuals** — errors follow normal distribution | Affects statistical tests |
| 5 | **No multicollinearity** — features not highly correlated | Unstable, uninterpretable coefficients |

---

### Q4. What evaluation metrics do you use for Linear Regression?

**Answer:**

| Metric | Formula | What It Tells You |
|---|---|---|
| **R²** | `1 - SS_res/SS_tot` | % of variance explained. 1.0 = perfect, 0 = no better than mean |
| **MAE** | `mean(\|y - ŷ\|)` | Average error in original units. Robust to outliers |
| **MSE** | `mean((y - ŷ)²)` | Penalizes large errors more. Sensitive to outliers |
| **RMSE** | `√MSE` | Same unit as target. Most commonly reported |

> R² is the primary metric. Use RMSE when large errors are unacceptable.

---

### Q5. What is the difference between Simple and Multiple Linear Regression?

**Answer:**
- **Simple:** One input feature → `y = w₀ + w₁x`
- **Multiple:** Multiple input features → `y = w₀ + w₁x₁ + ... + wₙxₙ`

Multiple Linear Regression can model more complex relationships but requires checking for multicollinearity between features.

---

### Q6. What are the strengths and limitations of Linear Regression?

| Strengths | Limitations |
|---|---|
| Simple, fast, interpretable | Assumes linear relationship |
| Coefficients show feature impact | Sensitive to outliers |
| Works well as a baseline model | Can't capture non-linear patterns |
| Low computational cost | Affected by multicollinearity |
| No tuning for basic form | No built-in regularization |

---

### Q7. What is multicollinearity and how do you handle it?

**Answer:**
Multicollinearity occurs when two or more features are highly correlated — e.g., height in cm and height in inches.

**Problems it causes:** Coefficients become unstable and hard to interpret. Small changes in data produce large swings in coefficients.

**How to detect:** Correlation matrix, Variance Inflation Factor (VIF > 5 is concerning)

**How to handle:**
- Remove one of the correlated features
- Use PCA to reduce dimensions
- Use Ridge Regression (adds L2 penalty — covered in SL009)

---

### Q8. Why do we scale features before Linear Regression?

**Answer:**
Feature scaling (StandardScaler) ensures all features contribute equally to the model. Without scaling:
- Coefficients are not directly comparable (a feature in thousands vs one in single digits)
- Gradient Descent converges slower

> Note: Scaling does NOT affect R² or prediction quality for OLS — it only affects coefficient interpretability and gradient descent convergence.

---

### Q9. What is the difference between Linear Regression and Logistic Regression?

| Aspect | Linear Regression | Logistic Regression |
|---|---|---|
| **Output** | Continuous value (e.g., 250,000) | Probability → class (0 or 1) |
| **Use case** | Regression problems | Classification problems |
| **Function** | Linear: `y = Xw` | Sigmoid: `σ(Xw)` |
| **Loss function** | MSE | Log loss (Binary Cross-Entropy) |
| **Evaluation** | R², RMSE, MAE | Accuracy, F1, ROC-AUC |

---

### Q10. What is R² and can it be negative?

**Answer:**
R² (coefficient of determination) measures how much variance in the target is explained by the model.

- **R² = 1.0:** Perfect prediction
- **R² = 0.0:** Model performs same as just predicting the mean
- **R² < 0:** Model performs WORSE than just predicting the mean — this happens on the test set when the model overfits the training set severely

> Yes, R² CAN be negative. It is not bounded at 0 for out-of-sample predictions.

---

## Tricky / Deep Questions

### T1. If R² is high on training but low on test, what is happening?

**Answer:** Overfitting. The model has learned noise in the training data and does not generalize. For Linear Regression, this is often caused by too many features relative to samples, or features that are noise. Solutions: remove irrelevant features, use Ridge/Lasso regularization (SL009), or get more data.

---

### T2. Can you use Linear Regression for classification?

**Answer:** Technically yes, but it is a bad idea. Linear Regression outputs continuous values, not bounded probabilities. Predicted values can go below 0 or above 1, and the decision boundary is highly sensitive to outliers. **Logistic Regression** is the correct choice for classification — it applies the sigmoid function to bound output between 0 and 1.

---

### T3. What happens if you don't use the intercept term (w₀)?

**Answer:** The regression line is forced through the origin (0, 0). This is only valid if the domain truly requires a zero prediction when all features are zero. In most cases, omitting the intercept introduces bias and reduces R². Always use `fit_intercept=True` (sklearn default) unless you have a specific domain reason.

---

### T4. What is the difference between OLS and Gradient Descent for Linear Regression?

| Aspect | OLS | Gradient Descent |
|---|---|---|
| **Method** | Closed-form matrix inversion | Iterative weight updates |
| **Speed** | Fast for small datasets | Better for very large datasets |
| **Complexity** | O(n²p + p³) | O(iterations × n × p) |
| **Exact solution** | Yes | Approximate (converges) |
| **Requires learning rate** | No | Yes |
| **Scales to big data** | No (matrix inversion breaks) | Yes (use SGD) |

---

### T5. How do you check if linear regression assumptions are met?

**Answer:**
1. **Linearity:** Scatter plot of X vs y; residuals vs fitted plot (should show no pattern)
2. **Independence:** Domain knowledge / Durbin-Watson test
3. **Homoscedasticity:** Residuals vs fitted (should be evenly spread, no fan shape)
4. **Normality of residuals:** Histogram of residuals, Q-Q plot
5. **Multicollinearity:** Correlation matrix, VIF scores

---

## Scenario-Based Questions

### S1. You trained a Linear Regression model on house prices. R² = 0.85 on train but 0.45 on test. What do you do?

**Steps:**
1. Check for data leakage (test data seen during training)
2. Check feature count vs sample count — reduce features
3. Check for highly correlated features — remove or combine
4. Apply Ridge or Lasso regularization (SL009)
5. Collect more training data
6. Try feature selection using correlation with target

---

### S2. A feature has a coefficient of -5.2. What does that mean?

**Answer:** For every 1 unit increase in that feature (after scaling), the predicted target decreases by 5.2 units. The sign shows direction; the magnitude shows importance. But only if features are scaled — otherwise coefficients in different units are not comparable.

---

### S3. Your residuals show a fan shape (variance increases with prediction). What does this mean?

**Answer:** This is **heteroscedasticity** — the variance of errors is not constant. Linear Regression assumes homoscedasticity. To fix:
- Apply log transformation to the target variable
- Use weighted least squares
- Use a different model (tree-based models don't have this assumption)

---

## Key Points to Remember

- Linear Regression finds `w = (XᵀX)⁻¹Xᵀy` — this is OLS
- R² measures explained variance, NOT prediction accuracy in absolute terms
- Scale features before comparing coefficients
- Residual plots are your best diagnostic tool
- Multicollinearity doesn't hurt predictions — only coefficient interpretability
- For regularization: Ridge (L2) keeps all features, Lasso (L1) can zero out features

---

## Common Mistakes to Avoid

| Mistake | Correct Approach |
|---|---|
| Not checking residuals | Always plot residuals vs predicted |
| Comparing unscaled coefficients | Scale with StandardScaler first |
| Using R² alone to judge the model | Use MAE/RMSE alongside R² |
| Forgetting to check for multicollinearity | Run correlation matrix and VIF |
| Applying to non-linear problems without checking | Plot X vs y first; use residuals to confirm |
| Reporting R² on training set only | Always report test set R² |

---

*Previous document: [TDD — SL001](../tdd/SL001_linear_regression_tdd.md)*
*Next document: [Learning — SL001](../learning/SL001_linear_regression_learning.md)*
