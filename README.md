# LSTM Stock-Price Forecaster

A lean, CPU-friendly notebook (`stock_price_prediction_with_LSTM.ipynb`) that predicts next-day closing prices for Apple (AAPL) using a stacked LSTM.

---

## Features
* **End-to-end pipeline** – data download → scaling → sequence prep → training → prediction → plot.  
* **Compact model** – two 50-unit LSTMs, one dense hidden layer (≈ 32 k params).  
* **Look-back window** – 60 trading days.  
* **Zero heavy dependencies** – just TensorFlow/Keras, yfinance, and scikit-learn.

---

## Quick Start

### 1 · Clone & install
```
git clone https://github.com/iamfaham/stock-price-prediction-LSTM.git
cd stock-price-prediction-LSTM
python -m venv .venv
source .venv/bin/activate         # Windows: .venv\Scripts\activate
```

### 2 · Run
```
jupyter notebook stock-price-prediction-LSTM.ipynb
```

Full run (10 epochs) finishes in ≈ 1 minute on a typical laptop CPU.

---

## Notebook Walk-through

| Step | What happens |
|------|--------------|
| **0 Setup** | Install yfinance & TensorFlow |
| **1 Imports** | Load libraries |
| **2 Fetch data** | Daily AAPL closes 2015-2025 |
| **3 Scale & split** | 80 % train / 20 % test, MinMax 0-1 |
| **4 Windowing** | 60-day sequences |
| **5 Model** | 50-50 LSTM + Dense-25 + Dense-1 |
| **6 Training** | 10 epochs, batch 64 |
| **7 Predict** | Inverse-scale outputs |
| **8 Plot** | Train vs Test vs Predicted |

---

## Results Snapshot
The forecast line tracks the unseen test data, with noticeable lag on sharp price spikes — expected for autoregressive single-feature LSTMs.

| Metric | Value |
|--------|-------|
| RMSE (USD) | 8.70 |
| MAE (USD)  | 6.89 |
| Accuracy (%) | 96.5 |


---

## Next Steps
* Add technical indicators or macro features.  
* Increase epochs & tune batch size.  
* Swap in GRU or Transformer encoders for longer context.  
* Serve via FastAPI for real-time inference.
