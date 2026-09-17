⚠️ FOR DYNAMIC, 3D PLOTS AND BEST EXPERIENCE please view the notebook on nbviewer or Google Colab, as GitHub's built-in viewer cannot render heavy interactive JavaScript or 3D plots. ⚠️

[View full notebook on NBViewer](https://nbviewer.org/github/barofrx-svg/github_datascience_projects/blob/main/project_6_kaggle_classification_competition/kaggle_competition.ipynb) or [View full notebook on Google Colab](https://colab.research.google.com/github/barofrx-svg/github_datascience_projects/blob/main/project_6_kaggle_classification_competition/kaggle_competition.ipynb)

# Kaggle Competition: Smartphone Addiction Prediction

## 1. Overview
This project tackles a Kaggle Playground/Prediction competition focused on modeling and predicting **smartphone addiction risk** based on behavioral metrics, usage statistics, and psychological indicators. The objective is to build a high-performance binary classification pipeline that accurately estimates user dependency categories while employing robust validation strategies to handle synthetic data artifacts and prevent overfitting.

---

## 2. Methodology & Architecture

- **Data Preprocessing & Feature Engineering:** 
  - Handled mixed tabular features, scaling numerical screen-time metrics and encoding categorical behavioral attributes.
  - Engineered new features from missingness information
- **Advanced Validation**
  - Implemented cross-validation schemes to mirror the competition's private test distribution.
- **Model Exploration & Hyperparameter Tuning:** 
  - Trained and benchmarked gradient-boosting frameworks including **XGBoost, LightGBM, and CatBoost**.
  - Optimized model hyperparameters via **Optuna** to maximize evaluation metrics (such as ROC-AUC and probability ranking accuracy).
- **Ensembling & Blending:** 
  - Combined predictions from diverse model architectures via weighted blending and stacking to maximize out-of-fold stability.

---

## 3. Results & Key Performance
- **Evaluation Metric:** Area Under the ROC Curve (ROC-AUC) / Probability Ranking.
- **Key Takeaways:** Discovered that managing feature artifacts and avoiding train-test leakage were far more critical to leaderboard performance than model complexity alone. Successfully built a high-scoring, stable gradient-boosting ensemble.

---

## 4. Tech Stack
- **Language:** Python
- **Libraries:** `pandas`, `NumPy`, `scikit-learn`, `XGBoost`, `LightGBM`, `CatBoost`, `Optuna`, `Seaborn`, `Matplotlib`

---

## 5. How to Run
```bash
# Run the training and inference pipeline
jupyter notebook kaggle_competition.ipynb
