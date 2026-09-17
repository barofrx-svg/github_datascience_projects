# Note!!
This file is too large for GitHub to render, please visit the following link. Nbviewer can handle 3d plots and large files in the browser:
[View full notebook on NBViewer](https://nbviewer.org/github/barofrx-svg/data_science_portfolio/blob/main/project_3_cement_strength_regression/project_3_c.ipynb)

# Multivariate Non-Linear Regression & Multi-Objective Optimization

## 1. Overview
This project models the non-linear compressive strength of concrete based on mix ingredients (cement, blast furnace slag, fly ash, water, superplasticizer, aggregates) and material age. It transitions from regularized linear models to gradient-boosted ensembles, utilizing custom objective functions, multi-objective Pareto optimization, and SHAP explainability.

---

## 2. Methodology & Key Workflows
- **Data Hygiene & Baseline Modeling:** Cleaned the dataset by dropping duplicate rows to prevent memorization bias. Benchmarked linear models against regularized linear architectures (`Ridge`, `Lasso`, `Elastic-Net`) to handle feature shrinkage and multicollinearity.
- **Custom Penalized Objectives & Multi-Objective Optimization:** 
  - Designed a custom Optuna objective function combining cross-validation mean error and fold variance ($\text{RMSE}_{\text{mean}} + e^{1.8 \cdot \text{std}}$) to penalize unstable models.
  - Executed multi-objective Bayesian optimization (`directions=['minimize', 'minimize']`) to simultaneously minimize validation RMSE and variance across folds, navigating the Pareto front for LightGBM, XGBoost, and CatBoost.
- **Model Explainability (SHAP):** 
  - Applied **SHAP (Shapley Additive exPlanations)** to decompose model predictions, quantifying exact global and local feature attributions for material age and cement concentration.

---

## 3. Results & Key Highlights
- Successfully captured complex, non-linear interactions between concrete components and curing age.
- Demonstrated advanced model tuning by balancing predictive accuracy with cross-validation stability.
- Delivered clear business driver insights via SHAP values, identifying non-linear threshold effects for cement and superplasticizers.

---

## 4. Tech Stack
- **Language:** Python
- **Libraries:** `pandas`, `NumPy`, `scikit-learn`, `LightGBM`, `XGBoost`, `CatBoost`, `Optuna`, `SHAP`, `Seaborn`, `Matplotlib`

---

## 5. How to Run
```bash
jupyter notebook project_3_c.ipynb
