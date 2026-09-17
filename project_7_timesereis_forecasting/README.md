⚠️ FOR DYNAMIC, 3D PLOTS AND BEST EXPERIENCE please view the notebook on nbviewer or Google Colab, as GitHub's built-in viewer cannot render heavy interactive JavaScript or 3D plots. ⚠️

[View full notebook on NBViewer](https://nbviewer.org/github/barofrx-svg/github_datascience_projects/blob/main/project_7_timesereis_forecasting/energy_consumption.ipynb) or [View full notebook on Google Colab](https://colab.research.google.com/github/barofrx-svg/github_datascience_projects/blob/main/project_7_timesereis_forecasting/energy_consumption.ipynb)

# Multi-Horizon Electricity Grid Demand Forecasting

## 1. Overview
This project builds deep learning architectures to forecast multi-horizon electricity grid load and demand patterns. The goal is to capture temporal dependencies and seasonal fluctuations across regional power grids using recurrent neural networks, drastically outperforming naive baseline forecasts.

---

## 2. Methodology & Architecture
- **Time-Series Data Engineering:** Cleaned high-frequency grid demand time-series data, engineered rolling lag features, and constructed sliding-window sequences for multi-step ahead forecasting.
- **Deep Learning Models:** Built and trained recurrent neural network architectures—specifically **LSTM (Long Short-Term Memory)** and **GRU (Gated Recurrent Unit)** networks—using TensorFlow/Keras.
- **Model Validation & Backtesting:** Evaluated models using time-series cross-validation splits to prevent data leakage and ensure realistic out-of-sample generalization.

---

## 3. Results & Key Highlights
- Achieved a **90.4% Mean Squared Error (MSE) reduction** compared to the naive persistence baseline.
- Successfully captured complex daily and weekly peak demand cycles across the electrical grid.
- Proved the efficacy of recurrent architectures for robust, multi-horizon operational forecasting.

Deep LSTM Model representation

#### Timeframe 1
<img width="1001" height="547" alt="before" src="https://github.com/user-attachments/assets/d8cd661a-3a92-4c00-b18f-8154fb88978c" />
<img width="1001" height="547" alt="prediction" src="https://github.com/user-attachments/assets/436246fb-9637-477f-838c-e29917144e8f" />
<img width="1001" height="547" alt="after" src="https://github.com/user-attachments/assets/3c95e3aa-67a4-4afe-bfd7-0e92de29b8e9" />

#### Timeframe 2
<img width="1001" height="547" alt="before2" src="https://github.com/user-attachments/assets/79a67c12-a5a6-4963-8d5d-2de51f5dacc0" />
<img width="1001" height="547" alt="prediction2" src="https://github.com/user-attachments/assets/ca0f4368-b7aa-442c-923b-5cfa40735159" />
<img width="1001" height="547" alt="after2" src="https://github.com/user-attachments/assets/82198264-9d37-4844-9339-0a0e8e04f0cc" />





---

## 4. Tech Stack
- **Language:** Python
- **Libraries:** `pandas`, `NumPy`, `TensorFlow`, `Keras`, `Scikit-learn`, `Matplotlib`, `Seaborn`

---

## 5. How to Run
```bash
jupyter notebook timeseries_forecasting.ipynb
