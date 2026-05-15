# 📈 Stock Direction Classifier — Equity Signal Model

A financial machine learning project predicting stock price direction 
using technical indicators, ensemble models and backtesting.
Built as part of my Data Science learning journey.

---

## 📌 Project Overview

This project investigates whether machine learning models can identify 
predictive patterns in historical stock market data and generate 
profitable trading signals. The system frames the problem as binary 
classification — will the stock close higher or lower tomorrow?

The project covers the complete quantitative finance ML workflow from 
data collection through backtesting and financial evaluation.

**Research Question:**
Can machine learning models use historical price and volume data to 
predict future stock direction well enough to create profitable 
trading strategies?

---

## 📂 Assets Analysed

| Ticker | Asset |
|---|---|
| AAPL | Apple |
| TSLA | Tesla |
| AMZN | Amazon |
| ^GSPC | S&P 500 Index |

20+ years of daily OHLCV data collected via yfinance.

---

## 🛠️ What Was Done

**Data Collection**
Collected historical daily market data from 2000 to 2026 for all 
four assets using the yfinance library. Tesla data begins from 2010 
due to its later IPO date.

**Feature Engineering**
Engineered 10 technical indicators from raw price and volume data:

| Feature | Purpose |
|---|---|
| Daily Return | Short-term momentum |
| SMA 5 | Short-term trend |
| SMA 20 | Medium-term trend |
| SMA 50 | Long-term trend |
| RSI | Momentum strength |
| MACD | Trend momentum |
| MACD Signal | Momentum confirmation |
| Volume Change | Trading activity |
| Volatility 10D | Market instability |
| Market Direction | S&P 500 previous day flag |

**Target Variable**
Binary classification label — 1 if tomorrow closes higher, 0 if lower. 
Calculated only from future price data after all features were 
engineered to prevent look-ahead bias.

**Time-Series Splitting**
Chronological 80/20 train/test split. No random shuffling. 
Training on oldest 80% of dates, testing on most recent 20%.

**Models Trained**
Random Forest Classifier as baseline and XGBoost Classifier as 
primary model.

**Backtesting**
Simulated directional trading strategy on test data. Compared 
cumulative returns against buy-and-hold benchmark. Evaluated using 
Sharpe Ratio for risk-adjusted performance.

---

## 📊 Model Results

| Ticker | RF Accuracy | RF AUC | XGB Accuracy | XGB AUC | Sharpe Ratio |
|---|---|---|---|---|---|
| AAPL | 0.653 | 0.515 | 0.671 | 0.491 | -0.80 |
| TSLA | 0.570 | 0.535 | 0.591 | 0.546 | -1.22 |
| AMZN | 0.622 | 0.568 | 0.630 | 0.564 | -2.78 |
| ^GSPC | 0.657 | 0.686 | 0.787 | 0.692 | -2.82 |

---

## 💡 Key Findings

The S&P 500 produced the strongest classification signal with XGBoost 
achieving AUC of 0.692 — indicating the model learned meaningful 
market structure beyond random guessing.

Tesla responded best to technical indicators due to its historically 
momentum-driven and volatile market behaviour.

All strategies produced negative Sharpe Ratios meaning returns were 
inconsistent and volatility outweighed profits. The strategies did 
not outperform simple buy-and-hold investing.

The most important lesson from this project is that prediction accuracy 
alone does not guarantee profitable trading. A model can be correct 
more than 65% of the time and still lose money.

---

## 🔑 Feature Importance

Top features driving model predictions across all assets:

1. RSI
2. MACD
3. MACD Signal
4. Volatility 10D
5. SMA 20
6. SMA 50
7. Daily Return
8. Volume Change
9. SMA 5
10. Market Direction

---

## ⚠️ Limitations

The current model has several limitations before production use:

No walk-forward validation — single chronological split only.
Limited feature set — no macroeconomic data or news sentiment.
Simple trading logic — no stop losses, position sizing or risk management.
No transaction cost modelling — slippage and commissions not fully accounted for.
No market regime detection — model does not adapt to bull, bear or sideways markets.

---

## 🚀 Potential Improvements

Walk-forward optimisation with rolling retraining windows.
Sentiment analysis from financial news and earnings reports.
LSTM or transformer models for sequence learning.
Reinforcement learning for dynamic position sizing.
Volatility regime detection and adaptive strategies.
Options flow and macroeconomic feature integration.

---

## 🧰 Tools & Libraries

- Python 3
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- yfinance
- ta
- mplfinance
- backtesting
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## 📁 File Structure
Stock-Direction-Classifier/
│
├── Notebook.ipynb                    # Complete analysis notebook
├── Stock_Direction_Classifier.docx   # Full project report
└── README.md                         # Project documentation

---

## 🎓 Corporate Project Brief

This project was structured as a corporate work assignment with 
five formal deliverables and strict deadlines:

| Deliverable | Description | Status |
|---|---|---|
| Learning Sign-Off Report | Concept understanding documentation | Done |
| Data Collection Report | Dataset exploration and cleaning | Done |
| Feature Engineering Report | Technical indicator development | Done |
| Model Training Report | Results and evaluation | Done |
| Backtesting Report | Strategy simulation and analysis | Done |

---

## 👤 Author

**Lindokuhle Nyoka**
Aspiring ML Engineer and Quantitative Analyst
[GitHub](https://github.com/lk-nyoka) · [LinkedIn](https://linkedin.com/in/lindokuhle-nyoka-982019245)# Stock-Direction-Classifier-Equity-Signal-Model
# Stock-Direction-Classifier-Equity-Signal-Model
