# Supervised Learning — Master Index

**Purpose:** Track learning progress across all Supervised Learning topics.
Each topic produces 4 documents + 1 Python implementation.
Dual goal: deep understanding + interview readiness.

---

## Progress Overview

| Done | Total | % Complete |
|------|-------|------------|
| 0    | 9     | 0% (SL001 In Progress) |

---

## Topic Index

| ID    | Algorithm                   | Type           | Difficulty | Status   | FDD | TDD | Interview | Learning | Code |
|-------|-----------------------------|----------------|------------|----------|-----|-----|-----------|----------|------|
| SL001 | Linear Regression           | Regression     | Beginner   | **In Progress** | ✓   | ✓   | ✓         | ✓        | ✓    |
| SL002 | Logistic Regression         | Classification | Beginner   | To Do    | —   | —   | —         | —        | —    |
| SL003 | Decision Tree               | Both           | Beginner   | To Do    | —   | —   | —         | —        | —    |
| SL004 | Random Forest               | Both           | Intermediate | To Do  | —   | —   | —         | —        | —    |
| SL005 | Support Vector Machine (SVM)| Both           | Intermediate | To Do  | —   | —   | —         | —        | —    |
| SL006 | K-Nearest Neighbors (KNN)  | Both           | Beginner   | To Do    | —   | —   | —         | —        | —    |
| SL007 | Gradient Boosting (XGBoost) | Both           | Advanced   | To Do    | —   | —   | —         | —        | —    |
| SL008 | Naive Bayes                 | Classification | Beginner   | To Do    | —   | —   | —         | —        | —    |
| SL009 | Ridge / Lasso Regression    | Regression     | Intermediate | To Do  | —   | —   | —         | —        | —    |

**Status values:** `To Do` → `In Progress` → `Done`
**Document values:** `—` = not created, `✓` = done

---

## Detailed Topic Breakdown

### SL001 — Linear Regression
- **Type:** Regression
- **When to use:** Predict a continuous numeric output
- **Key concepts:** Least squares, cost function, gradient descent, R², MSE
- **Dataset suggestion:** Boston Housing / California Housing / Custom salary dataset
- **Status:** In Progress
- **Documents:**
  - FDD: `fdd/SL001_linear_regression_fdd.md` ✓
  - TDD: `tdd/SL001_linear_regression_tdd.md` ✓
  - Interview: `interview/SL001_linear_regression_interview.md` ✓
  - Learning: `learning/SL001_linear_regression_learning.md` ✓
- **Code:** `ML/SL/SL001/linear_regression/linear_regression.ipynb` ✓

---

### SL002 — Logistic Regression
- **Type:** Classification (Binary / Multiclass)
- **When to use:** Predict a categorical output (0/1, Yes/No)
- **Key concepts:** Sigmoid function, log loss, decision boundary, precision/recall
- **Dataset suggestion:** Titanic survival / Breast cancer / Iris
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL002_logistic_regression_fdd.md`
  - TDD: `tdd/SL002_logistic_regression_tdd.md`
  - Interview: `interview/SL002_logistic_regression_interview.md`
  - Learning: `learning/SL002_logistic_regression_learning.md`
- **Code:** `ML/SL/SL002/logistic_regression.ipynb`

---

### SL003 — Decision Tree
- **Type:** Both (Regression + Classification)
- **When to use:** Need interpretable model, non-linear boundaries
- **Key concepts:** Gini impurity, entropy, information gain, pruning, tree depth
- **Dataset suggestion:** Iris / Titanic / Custom customer churn
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL003_decision_tree_fdd.md`
  - TDD: `tdd/SL003_decision_tree_tdd.md`
  - Interview: `interview/SL003_decision_tree_interview.md`
  - Learning: `learning/SL003_decision_tree_learning.md`
- **Code:** `ML/SL/SL003/decision_tree.ipynb`

---

### SL004 — Random Forest
- **Type:** Both (Regression + Classification)
- **When to use:** Reduce overfitting of Decision Tree, need feature importance
- **Key concepts:** Bagging, bootstrap sampling, ensemble, out-of-bag error
- **Dataset suggestion:** Titanic / House prices / Wine quality
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL004_random_forest_fdd.md`
  - TDD: `tdd/SL004_random_forest_tdd.md`
  - Interview: `interview/SL004_random_forest_interview.md`
  - Learning: `learning/SL004_random_forest_learning.md`
- **Code:** `ML/SL/SL004/random_forest.ipynb`

---

### SL005 — Support Vector Machine (SVM)
- **Type:** Both (Regression + Classification)
- **When to use:** High-dimensional data, small-to-medium datasets, clear margin
- **Key concepts:** Hyperplane, margin, support vectors, kernel trick (RBF, poly, linear)
- **Dataset suggestion:** Iris / Breast cancer / MNIST digits
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL005_svm_fdd.md`
  - TDD: `tdd/SL005_svm_tdd.md`
  - Interview: `interview/SL005_svm_interview.md`
  - Learning: `learning/SL005_svm_learning.md`
- **Code:** `ML/SL/SL005/svm.ipynb`

---

### SL006 — K-Nearest Neighbors (KNN)
- **Type:** Both (Regression + Classification)
- **When to use:** Simple baseline, local pattern matching, small datasets
- **Key concepts:** Euclidean/Manhattan distance, k value, lazy learner, curse of dimensionality
- **Dataset suggestion:** Iris / Digits / Custom recommendation
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL006_knn_fdd.md`
  - TDD: `tdd/SL006_knn_tdd.md`
  - Interview: `interview/SL006_knn_interview.md`
  - Learning: `learning/SL006_knn_learning.md`
- **Code:** `ML/SL/SL006/knn.ipynb`

---

### SL007 — Gradient Boosting / XGBoost
- **Type:** Both (Regression + Classification)
- **When to use:** Tabular data, competitions, need high accuracy
- **Key concepts:** Boosting, residuals, learning rate, n_estimators, regularization (L1/L2)
- **Dataset suggestion:** House prices / Titanic / Any structured Kaggle dataset
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL007_xgboost_fdd.md`
  - TDD: `tdd/SL007_xgboost_tdd.md`
  - Interview: `interview/SL007_xgboost_interview.md`
  - Learning: `learning/SL007_xgboost_learning.md`
- **Code:** `ML/SL/SL007/xgboost.ipynb`

---

### SL008 — Naive Bayes
- **Type:** Classification
- **When to use:** Text classification, spam detection, fast baseline
- **Key concepts:** Bayes theorem, conditional probability, independence assumption, Gaussian/Multinomial NB
- **Dataset suggestion:** SMS spam / 20 newsgroups / Sentiment analysis
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL008_naive_bayes_fdd.md`
  - TDD: `tdd/SL008_naive_bayes_tdd.md`
  - Interview: `interview/SL008_naive_bayes_interview.md`
  - Learning: `learning/SL008_naive_bayes_learning.md`
- **Code:** `ML/SL/SL008/naive_bayes.ipynb`

---

### SL009 — Ridge / Lasso Regression
- **Type:** Regression
- **When to use:** Linear regression with regularization, multicollinearity, feature selection
- **Key concepts:** L1 (Lasso) vs L2 (Ridge) penalty, alpha/lambda, coefficient shrinkage, ElasticNet
- **Dataset suggestion:** Boston Housing / Diabetes dataset / Custom feature-rich dataset
- **Status:** To Do
- **Documents:**
  - FDD: `fdd/SL009_ridge_lasso_fdd.md`
  - TDD: `tdd/SL009_ridge_lasso_tdd.md`
  - Interview: `interview/SL009_ridge_lasso_interview.md`
  - Learning: `learning/SL009_ridge_lasso_learning.md`
- **Code:** `ML/SL/SL009/ridge_lasso.ipynb`

---

## Learning Order (Recommended)

```
SL001 → SL002 → SL003 → SL004 → SL009 → SL006 → SL008 → SL005 → SL007
  │         │        │        │        │        │        │        │        │
Linear  Logistic  Decision  Random  Ridge/   KNN    Naive   SVM   XGBoost
Regress  Regress   Tree     Forest  Lasso          Bayes
```

**Rationale:**
1. SL001 → SL002: Linear → Logistic builds regression → classification intuition
2. SL003 → SL004: Tree → Forest shows bagging benefit
3. SL009: Regularization naturally follows linear models
4. SL006 → SL008: Simple non-parametric methods before complex ones
5. SL005 → SL007: Advanced/mathematically rich algorithms last

---

## Per-Topic Deliverables Checklist

For each topic, 5 deliverables must be completed:

- [ ] **FDD** — Functional Design Document (What + When + Use Cases)
- [ ] **TDD** — Technical Design Document (How + Math + Code Design)
- [ ] **Interview Doc** — 10+ Q&A, tricky questions, scenarios
- [ ] **Learning Doc** — EDA notes, experiment results, key insights
- [ ] **Python Code** — Working implementation (.ipynb) with train/eval

---

## Documents Created So Far

| Document Type | Count | Last Updated |
|---------------|-------|--------------|
| FDD           | 0/9   | —            |
| TDD           | 0/9   | —            |
| Interview     | 0/9   | —            |
| Learning      | 0/9   | —            |
| Code          | 0/9   | —            |

---

*Index maintained by: Product Owner Agent*
*Last updated: 2026-05-30*
