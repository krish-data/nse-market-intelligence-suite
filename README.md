# 📈 NSE Market Intelligence Suite: Institutional Flow & Sentiment Dashboard

## 🎯 Project Objective
![Live Market Impact Dashboard](dashboard.png)
A high-performance financial data engineering pipeline designed to analyze institutional activity (FII/DII) and price action within the National Stock Exchange (NSE) of India. This project tracks extreme institutional selling streaks and visualizes market sentiment to provide actionable trading intelligence.

## 🛠️ The Tech Stack
* **Languages:** Python 3.10
* **Data Engineering:** Pandas (ETL, Data Wrangling, Relational Merges)
* **Visualization:** Plotly Graph Objects & Subplots (Interactive Dual-Axis Dashboards)
* **Environment:** VS Code + Jupyter Notebooks
* **Infrastructure:** Local Git Repository -> GitHub

## 📡 Data Strategy
* **Primary Sources:** NSE / MoneyControl (Institutional Equity Cash Flow) & Nifty 50 Historical Prices.
* **Frequency:** Daily Automated Pipeline (Post-market updates).
* **Master Database:** A unified, sanitized CSV containing merged historical logs from Jan 2026 to Present.

## 🏗️ Project Architecture (Current Progress: Day 7)

### Phase 1: Data Engineering (COMPLETED)
* **ETL Pipeline:** Built a robust cleaning engine to bypass raw data formatting issues. The script automatically handles:
  * Removal of currency commas and whitespace stripping.
  * Type conversion from Strings to Numeric floats.
  * Automated skipping of junk website headers and `NaN` handling.
* **Relational Data Merge:** Engineered an `inner join` using Pandas to seamlessly zipper daily Nifty 50 closing prices with institutional flow data.
* **Incremental Logic:** Developed an automated "Daily Update" engine that ingests staging files, removes duplicates, and overwrites the `master_database.csv`—acting as the "Single Source of Truth."

### Phase 2: Intelligence & Visualization (COMPLETED)
* **Interactive Market Dashboard:** Upgraded from static Matplotlib to a dynamic Plotly dashboard featuring a dual-axis layout (Bar charts for Crores, Line charts for Index points) with unified hover-tooltips.
* **Proprietary Signal Logic:** * **Streak Counter:** A custom Python function that iterates through time-series data to calculate consecutive days of institutional buying or selling.
  * **Net Sentiment Gauge:** An automated calculator that measures the "Tug-of-War" between FIIs and DIIs to output a daily Bullish/Bearish market sentiment alert.
  * **Volatility Gauge (Z-Score):** A statistical algorithm calculating the standard deviation of FII cash flow to identify extreme mathematical anomalies (e.g., Z-scores of -2.0+ indicating panic sell-offs).

## 📂 Repository Structure
```text
├── data/
│   ├── fii_dii_master_database.csv  <-- Unified history & Nifty prices
│   ├── nifty50.csv                  <-- Raw index closing prices
│   ├── fii_history_2026-02.csv      <-- Original Feb history
│   ├── fii_raw_jan_2026.csv         <-- Jan staging file
│   └── fii_raw_march_2026.csv       <-- March staging file
├── notebooks/
│   └── 03_fii_dii_master.ipynb      <-- Primary Engine (ETL, Merge, Visuals, Logic)
├── dashboard.png                    <-- Static Hero Image for GitHub rendering
└── README.md