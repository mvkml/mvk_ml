# Learning Notes — SL001: Linear Regression

**Document Type:** Learning / Experiment Log
**Topic ID:** SL001
**Algorithm:** Linear Regression
**Owner:** Dev Data Agent
**Created:** 2026-05-30
**Status:** In Progress — fill this after running the notebook

---

## 1. Concept Summary

Linear Regression fits the best-fit line through data by minimizing MSE. The model learns weights (w) and an intercept (w₀) such that `ŷ = w₀ + w₁x₁ + ... + wₙxₙ`.

**Key insight:** The coefficients tell you the direction and magnitude of each feature's impact on the target, assuming all other features are held constant.

---

## 2. Dataset Used

| Detail | Value |
|---|---|
| **Name** | California Housing |
| **Source** | `sklearn.datasets.fetch_california_housing` |
| **Rows** | 20,640 |
| **Features** | 8 numeric |
| **Target** | `MedHouseVal` — Median house value (in $100,000 units) |
| **Missing values** | None |

### Feature Descriptions

| Feature | Description |
|---|---|
| `MedInc` | Median income in block group |
| `HouseAge` | Median house age |
| `AveRooms` | Average number of rooms per household |
| `AveBedrms` | Average number of bedrooms per household |
| `Population` | Block group population |
| `AveOccup` | Average number of household members |
| `Latitude` | Block group latitude |
| `Longitude` | Block group longitude |

---

## 3. EDA Observations

> Fill this section after running the notebook EDA cells.

- [ ] Target distribution: is `MedHouseVal` normally distributed or skewed?
- [ ] Which feature has the highest correlation with target?
- [ ] Are there any outliers in `AveRooms` or `AveBedrms`?
- [ ] Do `Latitude` and `Longitude` show geographic clustering?
- [ ] Is `MedInc` the dominant predictor visually?

---

## 4. Preprocessing Steps

| Step | Code | Why |
|---|---|---|
| Train/test split | `train_test_split(X, y, test_size=0.2, random_state=42)` | Hold out 20% for unbiased evaluation |
| Feature scaling | `StandardScaler().fit_transform(X_train)` | Makes coefficients comparable; required for fair gradient interpretation |
| No imputation needed | — | California Housing has no missing values |

---

## 5. Model Configuration

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression(
    fit_intercept=True,   # Learn bias term w₀
    copy_X=True,          # Default — don't modify original X
    n_jobs=None           # Single core for this dataset size
)
model.fit(X_train_scaled, y_train)
```

---

## 6. Results

> Fill this section after running the notebook.

| Metric | Train Set | Test Set |
|---|---|---|
| R² | — | — |
| MAE | — | — |
| MSE | — | — |
| RMSE | — | — |

### Coefficients (after scaling)

| Feature | Coefficient | Direction |
|---|---|---|
| MedInc | — | — |
| HouseAge | — | — |
| AveRooms | — | — |
| AveBedrms | — | — |
| Population | — | — |
| AveOccup | — | — |
| Latitude | — | — |
| Longitude | — | — |
| **Intercept** | — | — |

---

## 7. Visualization Notes

> Fill after running the notebook.

- [ ] **Actual vs Predicted scatter:** Points tightly around diagonal line? Or spread?
- [ ] **Residuals vs Predicted:** Random scatter (good) or fan shape (heteroscedasticity)?
- [ ] **Residuals histogram:** Bell-shaped (good) or skewed?
- [ ] **Coefficient bar chart:** Which feature has largest positive / negative impact?

---

## 8. Key Insights

> Fill after analysis.

- [ ] Which feature turned out to be the most important predictor?
- [ ] Did scaling change which features appeared most impactful?
- [ ] Was the linearity assumption satisfied? (Check residuals plot)
- [ ] Were there any surprising coefficient directions?
- [ ] What is the practical meaning of the RMSE in the domain context?

---

## 9. What I'd Do Differently / Next Steps

- [ ] Try removing `Latitude` and `Longitude` — are they helping or hurting?
- [ ] Apply log transformation to target if residuals are skewed
- [ ] Compare with Ridge/Lasso (SL009) to see if regularization helps
- [ ] Try Polynomial features on `MedInc` to capture non-linearity
- [ ] Check VIF scores for multicollinearity between `AveRooms` and `AveBedrms`

---

## 10. References

| Resource | Link / Location |
|---|---|
| sklearn LinearRegression docs | https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html |
| California Housing dataset info | https://scikit-learn.org/stable/datasets/real_world.html#california-housing-dataset |
| FDD | `documents/fdd/SL001_linear_regression_fdd.md` |
| TDD | `documents/tdd/SL001_linear_regression_tdd.md` |
| Interview | `documents/interview/SL001_linear_regression_interview.md` |
| Notebook | `ML/SL/SL001/linear_regression/linear_regression.ipynb` |

---

*Owner: Dev Data Agent*
*Update this document after completing the notebook and running experiments.*
