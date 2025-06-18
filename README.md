# Stock-Price Prediction with LSTM

A concise, CPU-friendly notebook (`stock_price_prediction_with_LSTM.ipynb`) that demonstrates how stacked LSTM networks can forecast daily closing prices for a chosen stock ticker.

---

## Table of Contents
1. Features  
2. Quick Start  
3. Project Structure  
4. Notebook Walk-through  
5. Results Snapshot  
6. Next Steps  
7. License  

---

## Features
* **End-to-end pipeline** – data download, scaling, sequence prep, model training, evaluation, future forecasting.  
* **Stacked LSTM** – captures both short and mid-term temporal dependencies.  
* **Visual diagnostics** – training-loss curves, predicted-vs-actual plot, future forecast.  
* **Minimal dependencies** – TensorFlow/Keras, pandas, yfinance, scikit-learn.

---

## Quick Start

### 1 · Clone and install
code
git clone https://github.com/<your-user>/lstm-stock-forecast.git
cd lstm-stock-forecast
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
code

### 2 · Run the notebook
code
jupyter notebook stock_price_prediction_with_LSTM.ipynb
code

> **Tip:** The full run (20 epochs) takes < 2 minutes on a typical laptop CPU.

---

## Project Structure
code
lstm-stock-forecast/
│
├─ stock_price_prediction_with_LSTM.ipynb   ← Main notebook
├─ requirements.txt                         ← Package list
└─ README.md                                ← You are here
code

---

## Notebook Walk-through

| Section | Purpose |
|---------|---------|
| **1 Fetch data** | Pull 10+ years of OHLCV data via `yfinance`. |
| **2 EDA** | Trend & volatility plots for sanity check. |
| **3 Split & scale** | Chronological 80/20 split, MinMax scaling. |
| **4 Sequence build** | Convert to `(samples, 60, 1)` tensors. |
| **5 Model** | Two LSTM layers + dense output. |
| **6 Training** | Adam, MSE loss, early-stopping. |
| **7 Evaluation** | RMSE, R² on test data. |
| **8 Forecast** | Next-30-day projection. |
| **Conclusion** | Take-aways & upgrade ideas. |

---

## Results Snapshot
| Metric | Value |
|--------|-------|
| RMSE (USD) | ~ 1.45 |
| R² Score | 0.95 |
| Forecast horizon | 30 trading days |

The model tracks price direction well, though it lags during sudden jumps (a common LSTM trait).

---

## Next Steps
* **Feature enrichment** – add technical indicators or macro-economic signals.  
* **Model variants** – try GRU, CNN-LSTM, or Transformer encoders.  
* **Hyper-parameter search** – automate tuning with Keras-Tuner or Optuna.  
* **Production** – wrap scaler + model in FastAPI for real-time inference.

---

## License
Released under the MIT License – see `LICENSE` for details.
