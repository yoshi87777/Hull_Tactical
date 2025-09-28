# Hull Tactical - Market Prediction

## 📖 Overview
This repository contains work for the **Kaggle Hull Tactical Market Prediction Competition**.  
The goal is to predict **daily excess returns of the S&P 500** and design a **betting strategy (0–2 leverage)** that maximizes risk-adjusted performance under a **120% volatility constraint**.  

---

## 📂 Dataset Description

### Training Data (`train.csv`)
- `date_id` – Identifier for a trading day  
- `M*` – Market dynamics / technical features  
- `E*` – Macro economic features  
- `I*` – Interest rate features  
- `P*` – Price/valuation features  
- `V*` – Volatility features  
- `S*` – Sentiment features  
- `MOM*` – Momentum features  
- `D*` – Dummy/binary features  
- `forward_returns` – One-day forward returns of the S&P 500  
- `risk_free_rate` – Federal funds rate  
- `market_forward_excess_returns` – Forward returns relative to 5-year rolling mean (MAD winsorized)  

### Test Data (`test.csv`)
- `date_id` – Identifier for a trading day  
- Feature columns identical to `train.csv`  
- `is_scored` – Indicates whether the row is used in evaluation  
- `lagged_forward_returns` – Forward returns with a one-day lag  
- `lagged_risk_free_rate` – Risk-free rate with a one-day lag  
- `lagged_market_forward_excess_returns` – Excess returns with a one-day lag  

### Evaluation API (`kaggle_evaluation/`)
- Used for official submission and evaluation  
- Feeds unseen market data sequentially to simulate live trading  

---

## 🔄 Competition Phases

1. **Training Phase**  
   - Train models using historical data  
   - Public leaderboard based on last 180 trading days  
   - Scores during this phase are *not* meaningful for final ranking  

2. **Forecasting Phase**  
   - After the submission deadline, models are run on unseen real-world data  
   - Leaderboard updates periodically as new market data becomes available  

---

## 📈 Evaluation Metric
- Variant of the **Sharpe ratio**  
- Penalizes:  
  - Excess volatility (> 120% of S&P 500)  
  - Underperformance vs. benchmark  

**Submission format:**  
- For each trading day, output portfolio weight `w` where:  

---

## ⚙️ Project Structure

```text
HullTactical/
│── data/
│   ├── train.csv
│   ├── test.csv
│   └── kaggle_evaluation/
│
│── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Baseline_LGBM.ipynb
│   ├── 03_Feature_Engineering.ipynb
│   └── 04_Ensemble_Strategy.ipynb
│
│── src/
│   ├── features.py        # Feature engineering
│   ├── models.py          # Model definitions
│   ├── strategy.py        # Position sizing logic
│   └── evaluation.py      # Sharpe ratio reproduction
│
│── README.md
└── requirements.txt
```

---

## ✅ To Do
- [ ] Data preprocessing (missing values, normalization)  
- [ ] Baseline model (LightGBM)  
- [ ] Feature engineering (momentum, volatility, rates)  
- [ ] Validation framework (rolling CV + Sharpe reproduction)  
- [ ] Ensemble strategy  
- [ ] Final submission notebook  

---

## 📚 References
- [Hull Tactical - Market Prediction (Kaggle)](https://www.kaggle.com/competitions/hull-tactical-market-prediction)  
- Blair Hull et al. (2025). *Competition Documentation*  

---
