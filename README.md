# SPY-ROI-120d-ML-Model

Machine learning model to estimate the probability that SPY will achieve a
6-month forward return greater than +5%.  
The project includes full feature engineering, model training, evaluation,
interpretation, and reproducibility steps.

---

## 📌 Project Overview

This project builds a predictive model for medium-term market performance using
a combination of trend, momentum, and volatility features engineered from SPY
daily data.

**Goal:**  
Predict whether the **120-day forward ROI exceeds +5%** and produce a probability
estimate that can be used for filtering, position sizing, or regime detection.

This is a realistic financial ML task where long-horizon predictions are noisy,
and therefore proper feature engineering and evaluation methodology are crucial.

---

## 📊 Key Results

After full preprocessing, feature engineering, and threshold optimization, the
Random Forest classifier achieved:

| Metric | Value |
|--------|--------|
| **Accuracy** | 71.5% |
| **Precision** | 62.2% |
| **Recall** | 68.7% |
| **ROC AUC** | 0.664 |

These are strong and realistic metrics for a 6-month predictive horizon in
financial markets.

The optimized threshold (Youden’s J statistic) significantly improved recall and
precision compared to the default 0.50 cutoff.

---

## 🧠 Feature Engineering

The model uses financial features that capture market structure and regime behavior.
All features were engineered manually using pandas.

### Trend Features
- SMA50  
- SMA200  
- Price distance to SMAs  
- SMA50/SMA200 ratio  
- SMA slopes  
- Golden/Death Cross signal  

### Momentum Features
- ROC90  
- ROC120  
- RSI28  

### Volatility Features
- ATR50 / ATR100  
- Normalized ATR  
- Bollinger Bands 50 & 100 (upper, mid, lower, width, std)

---

## 🔍 Feature Importance Insights

Both impurity-based and permutation importance highlight the same core predictors:

### Top Features
- BB100_upper  
- SMA200  
- BB50_std  
- ATR100 / ATR50  
- SMA50  
- ROC120  

These results align with academic and empirical literature:  
**long-term trend + volatility structure are the strongest predictors of future returns.**

---

## 🧪 Model Evaluation

The model was evaluated using:
- TimeSeriesSplit  
- Full metrics (accuracy, precision, recall, ROC AUC)  
- Threshold optimization (Youden’s J)  
- Confusion matrices before & after optimization  

Visual outputs (in `reports/figures/`):
- Feature Importance (impurity-based)  
- Permutation Importance  
- Confusion Matrix  
- Optimized Confusion Matrix  

---

## 📁 Repository Structure

```SPY-ROI-120d-ML-Model/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│
├── src/
│
├── reports/
│   └── figures/
│
├── requirements.txt
├── LICENSE
└── README.md```



## ▶️ How to Run the Project

1. Clone the repository

git clone https://github.com/hernaninv/SPY-ROI-120d-ML-Model.git

2. Install dependencies

pip install -r requirements.txt

3. Open the notebook

Open the file:
notebooks/SPY_ROI_120d_Model.ipynb
Run all cells to reproduce feature engineering, model training, threshold optimization, and evaluation.

💡 What This Project Demonstrates

This project highlights my ability to:

Engineer domain-specific financial features

Apply ML models correctly to chronological data

Avoid look-ahead bias using proper validation

Perform threshold optimization

Interpret model behavior with feature importance

Communicate insights clearly for business and investment contexts

📬 Contact

Feel free to reach out if you'd like to discuss ML, financial analytics, time-series modeling, or data-driven research.
