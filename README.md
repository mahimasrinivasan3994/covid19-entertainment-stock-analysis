# 🎬 COVID-19 Pandemic Stock Market Reactions — Visual Entertainment Industry

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Power BI](https://img.shields.io/badge/PowerBI-F2C811?logo=powerbi&logoColor=black)
![Yahoo Finance](https://img.shields.io/badge/Data-Yahoo%20Finance-purple)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> **Analyzing how the COVID-19 pandemic reshaped stock market behavior across streaming giants and traditional entertainment firms — and what it means for investors navigating economic crises.**

---

## 📌 Problem Statement

The COVID-19 pandemic triggered unprecedented disruption across global industries. Within the visual entertainment sector, this disruption was uniquely **bifurcated**: streaming services surged as audiences moved online, while cinema chains and live event companies faced severe revenue losses due to lockdowns and closures.

This project investigates:
- How did adjusted close prices and trading volumes of entertainment stocks behave during each wave?
- Was there a statistically meaningful difference in market performance between the **first wave (Jan–Jun 2020)** and the **second wave (Jul–Dec 2020)**?
- Did streaming firms consistently outperform traditional entertainment companies — and by how much?

Understanding these dynamics equips investors and industry stakeholders with evidence-based insight for future crisis-preparedness.

---

## 🎯 Research Objectives

| # | Objective |
|---|-----------|
| 1 | Examine fluctuations in adjusted close prices and trading volumes across **15 firms** during both pandemic waves |
| 2 | Identify significant differences in stock market performance between Wave 1 and Wave 2 |
| 3 | Provide data-driven insights into investor behavior and market resilience |

**Research Questions:**
- **RQ1:** What is the impact of COVID-19 on the trading volume of visual entertainment stocks?
- **RQ2:** What is the difference in adjusted close prices and trading volume between the first and second waves of COVID-19?

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        DATA PIPELINE                            │
│                                                                 │
│   Yahoo Finance API                                             │
│        │                                                        │
│        ▼                                                        │
│   yfinance (Python)  ──►  Raw Stock Data (15 Firms, 2020)      │
│        │                                                        │
│        ▼                                                        │
│   Pandas (Data Cleaning & Feature Engineering)                  │
│        │                                                        │
│        ▼                                                        │
│   CSV Export (Stock_Market_Data.csv)                            │
│        │                                                        │
│        ▼                                                        │
│   Power BI (DAX Transformations + Visualizations)               │
│        │                                                        │
│        ├──► Correlation Analysis                                │
│        ├──► Trend Analysis                                      │
│        └──► Comparative Analysis (Wave 1 vs Wave 2)            │
└─────────────────────────────────────────────────────────────────┘
```

---

## 💡 Solution Approach

### 1. Data Collection
- Pulled daily OHLCV stock data for **15 firms** from Yahoo Finance using `yfinance`
- Covered the full year **January 1 – December 31, 2020**
- Segmented into:
  - **Wave 1:** Jan 1 – Jun 30, 2020
  - **Wave 2:** Jul 1 – Dec 31, 2020

### 2. Company Coverage

| Category | Companies (Ticker) |
|----------|-------------------|
| **Streaming** | Netflix (NFLX), Disney (DIS), Warner Bros. Discovery (WBD), Roku (ROKU), Sony (SONY), Warner Music Group (WMG) |
| **Traditional** | Comcast (CMCSA), Cinemark (CNK), IMAX (IMAX), Fox Corp (FOXA), Live Nation (LYV), TKO Group (TKO), Lionsgate (LGF-B), Liberty Media (FWONA), Paramount (PARA) |

### 3. Data Cleaning (Power BI + Python)
- Handled missing values via forward-fill / backward-fill
- Standardized date formats for time-series accuracy
- Created `CompanyCategory` column (DAX) to classify firms as Streaming vs Traditional
- Verified complete data across both waves for all 15 companies

### 4. Analytical Methods

| Method | Purpose |
|--------|---------|
| **Correlation Analysis** | Measured relationship strength between adjusted close prices and trading volumes |
| **Trend Analysis** | Tracked price and volume patterns monthly across both waves |
| **Comparative Analysis** | Evaluated Wave 1 vs Wave 2 differences using Power BI bar chart visualizations |

---

## 📊 Results & Key Findings

### 🔗 Correlation Analysis
| Scope | Finding |
|-------|---------|
| Overall | Strong positive correlations within the same industry segment |
| Wave 1 | **Weaker correlations** — elevated market uncertainty, independent stock movements |
| Wave 2 | **Stronger correlations** — synchronized market reaction, investor adaptation |
| Streaming stocks | Consistently higher correlations across both waves |
| Traditional stocks | Shifted from weak (Wave 1) to stronger (Wave 2) correlations |

### 📈 Trend Analysis
- **Streaming firms**: Sustained upward price trends — confirmed strong investor confidence in digital content
- **Traditional firms**: Initial steep decline in Wave 1, followed by partial recovery in Wave 2 as reopening strategies emerged
- First wave exhibited **high volatility**; second wave showed a **more stable, steady trend**

### 📉 Comparative Analysis (Wave 1 vs Wave 2)
| Metric | Wave 1 | Wave 2 |
|--------|--------|--------|
| Adjusted Close Prices | Lower (market shock) | Notably higher (investor stabilization) |
| Trading Volume | Higher (panic/reactive trading) | Lower (market stabilization) |
| Streaming Performance | Resilient | Consistently strong |
| Traditional Performance | Sharp decline | Slow recovery |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python 3.x** | Data extraction and preprocessing |
| **yfinance** | Yahoo Finance API for stock data retrieval |
| **Pandas** | Data cleaning, transformation, and structuring |
| **Power BI** | DAX formulas, interactive dashboards, visualizations |
| **CSV / Excel** | Intermediate data storage and export |

---

## 📁 Project Structure

```
covid19-entertainment-stocks/
│
├── data/
│   └── Stock_Market_Data.csv          # Cleaned stock data for all 15 firms
│
├── notebooks/
│   └── data_extraction.ipynb          # yfinance data pull + Pandas preprocessing
│
├── powerbi/
│   └── entertainment_stocks.pbix      # Power BI dashboard file
│
├── visuals/
│   ├── correlation_analysis.png
│   ├── trend_wave1_vs_wave2.png
│   └── comparative_bar_charts.png
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install yfinance pandas openpyxl
```

### Run Data Extraction
```python
import yfinance as yf
import pandas as pd

tickers = ["NFLX", "DIS", "WBD", "ROKU", "SONY", "WMG",
           "CMCSA", "CNK", "IMAX", "FOXA", "LYV", "TKO", "LGF-B", "FWONA", "PARA"]

data = yf.download(tickers, start="2020-01-01", end="2020-12-31")
data.to_csv("data/Stock_Market_Data.csv")
```

### Power BI Setup
1. Open `powerbi/entertainment_stocks.pbix` in Power BI Desktop
2. Refresh data source pointing to `data/Stock_Market_Data.csv`
3. Navigate tabs: Correlation | Trends | Wave Comparison

---

## ⚠️ Limitations

- Dataset limited to **15 firms** — may not fully represent the broader visual entertainment industry
- External factors (government stimulus policies, vaccine rollout announcements) may have influenced stock trends beyond COVID-19 alone
- Power BI lacks formal statistical testing (e.g., Wilcoxon Signed-Rank Test) — comparative analysis is visualization-based
- Study is confined to **2020 only** — a longer time horizon would reveal sustained post-pandemic recovery trends

---

## 🌍 Project Impact

| Stakeholder | Benefit |
|-------------|---------|
| **Investors** | Evidence that streaming stocks serve as safer assets during economic downturns |
| **Traditional Entertainment Firms** | Data-backed case for digital diversification as crisis mitigation |
| **Financial Analysts** | Framework for sector-specific behavioral analysis during systemic shocks |
| **Academic Research** | Contributes empirical evidence on market dynamics in crisis conditions |

**Key Takeaway:** Digital adaptability is the single strongest predictor of stock market resilience during pandemic-era disruption. Streaming firms did not just survive — they demonstrated that crisis conditions can be a growth catalyst when business models align with changing consumer behavior.

---

## 📚 References

- Baker, S.R., et al. (2020). *The Unprecedented Stock Market Reaction to COVID-19.* NBER Working Paper.
- Zhang, et al. (2022). *COVID-19's impact on stock returns in cultural and entertainment industries.* Journal of Financial Economics.
- Luo, X. (2020). *The Streaming Wars: Digital Entertainment during COVID-19.*
- Shah, et al. (2020). *Cinemas and COVID-19: Regional recovery differences in the global film industry.*
- Ryu, S. & Cho, Y. (2022). *Pandemic-induced business model changes: A framework for financial resilience.*
- Yahoo Finance: https://finance.yahoo.com
- yfinance Documentation: https://pypi.org/project/yfinance/

---

## 👤 Author

**[Mahima Srinivasan]**
- 📧 [mahima.s3994@gmail.com.com]
- 💼 [linkedin.com/in/mahimasrinivasan3994]

> *This project was developed as part of a data analytics portfolio demonstrating skills in financial data analysis, Python-based data engineering, and business intelligence visualization.*

---

*⭐ If you found this project insightful, please consider starring the repository!*
