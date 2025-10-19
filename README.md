# 💼 Applied Volatility Modeling & Value-at-Risk Backtesting

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Finance](https://img.shields.io/badge/Finance-Risk%20Modeling-green)
![Volatility](https://img.shields.io/badge/Model-GARCH-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📊 Project Overview
This project applies **volatility modeling and risk estimation techniques** to equity markets using **GARCH-family models**.  
The goal is to measure and backtest the **Value-at-Risk (VaR)** of different market indices, focusing on real-world financial risk management applications.

We compare volatility dynamics and risk performance between the **U.S. (S&P 500)** and the **U.K. (FTSE 100)** markets over a **30-year period (1990–2021)**.

---

## 🎯 Objectives
- Model and forecast market volatility using **ARCH / GARCH / EGARCH** models.  
- Estimate **1-day ahead Value-at-Risk (VaR)** at multiple confidence levels (95%, 99%).  
- Conduct **backtesting** using Kupiec and Christoffersen tests to evaluate VaR model performance.  
- Compare volatility persistence and risk behavior between different markets.

---

## 🧩 Methodology

### 1️⃣ Data Preparation
- Daily closing prices of **S&P 500** and **FTSE 100** indices (1990–2021).  
- Returns computed as log differences.  
- Normality tests show heavy tails → justify the use of GARCH-family models.

### 2️⃣ Volatility Modeling
| Model | Description | Key Feature |
|--------|--------------|-------------|
| **ARCH(q)** | Autoregressive conditional heteroskedasticity | Captures time-varying volatility |
| **GARCH(1,1)** | Generalized ARCH | Adds lagged volatility term for persistence |
| **EGARCH(1,1)** | Exponential GARCH | Captures leverage effects (asymmetric volatility) |

### 3️⃣ Risk Estimation
- **Value-at-Risk (VaR)** computed from model-fitted volatility:
VaR_t = μ_t + z_α * σ_t
where `z_α` is the quantile from the assumed distribution.

### 4️⃣ Backtesting
- **Kupiec Test (Unconditional Coverage)** → checks if observed violations ≈ expected  
- **Christoffersen Test (Conditional Coverage)** → checks independence of violations  

---

## 📈 Key Results

| Market | Best Model | 99% VaR Violations | Kupiec p-value | Christoffersen p-value |
|---------|-------------|--------------------|----------------|------------------------|
| **S&P 500 (US)** | GARCH(1,1) | 2.3% | 0.47 | 0.62 |
| **FTSE 100 (UK)** | EGARCH(1,1) | 1.8% | 0.53 | 0.70 |

✅ **Interpretation:**
- Both models provide statistically valid VaR forecasts (fail to reject H0 at 5%).  
- EGARCH performs slightly better in capturing downside asymmetry in UK market volatility.  
- Volatility persistence is higher in S&P 500, consistent with U.S. market stability post-2008.  

---

## 💡 Insights & Takeaways

1. **Volatility Clustering:** Financial markets exhibit clear volatility clustering — GARCH captures this effectively.  
2. **Leverage Effect:** Negative shocks increase volatility more than positive ones (EGARCH evidence).  
3. **Model Robustness:** GARCH(1,1) and EGARCH(1,1) remain industry-standard tools for daily risk estimation.  
4. **Risk Management Relevance:** Accurate VaR forecasts are crucial for capital allocation, stress testing, and compliance (e.g. Basel III).  
5. **Cross-Market Observation:** U.S. market volatility is more persistent, while UK market shows stronger asymmetry.

---

## 🧠 Future Extensions
- Apply **Student-t GARCH** or **GJR-GARCH** to better model fat tails.  
- Extend VaR horizon to 10-day or 30-day periods.  
- Integrate **cryptocurrency or emerging markets** for comparative analysis.  
- Build a **real-time VaR dashboard** using Streamlit or Dash.

---

## 🧰 Tech Stack
- **Python:** `arch`, `statsmodels`, `pandas`, `matplotlib`, `scipy`
- **Data:** Yahoo Finance (via `yfinance`)
- **Backtesting:** Kupiec & Christoffersen tests implemented manually and via `arch` library

---

## 📂 Repository Structure
📁 avm-volatility-modeling/
├── data/ # Price & return series
├── notebooks/ # Jupyter notebooks for modeling
├── results/ # Model summary tables, VaR violations, plots
├── AVM-Project-TuNgocLien-VoDucToan.pdf # Full report
└── README.md # Documentation

---

## 👨‍💻 Authors
- **Ngọc Liên**  
- **Đức Toàn** ([@toanvoduc27](https://github.com/toanvoduc27))  
📊 Université Paris 1 Panthéon-Sorbonne  
Supervised by *Sylvain Barthélémy*

---

## 📝 License
This project is licensed under the [MIT License](LICENSE).

---

> *“Volatility is not risk itself — it’s the visible pulse of how markets digest uncertainty.”*
