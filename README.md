📈 NSE Market Intelligence Suite
An Institutional Flow Analysis & Predictive Short-Covering Model

🎯 Project Objective
A high-performance financial data engineering pipeline designed to analyze institutional activity and volatility metrics within the National Stock Exchange (NSE) of India. This project identifies extreme institutional selling streaks that historically precede "Short-Covering" market rallies.

🛠️ The Tech Stack
Languages: Python 3.10

Libraries: Pandas (Data Wrangling), Matplotlib (Visualization)

Environment: VS Code + Jupyter Notebooks

Infrastructure: Local Git Repository

📡 Data Strategy
Primary Source: MoneyControl (Institutional Equity Cash Flow)

Frequency: Daily Incremental Updates (11:00 PM IST)

Master Database: A unified, sanitized CSV containing historical logs from Jan 2026 to Present.

🏗️ Project Architecture (Current Progress: Day 3/16)
Phase 1: Engineering (COMPLETED)
ETL Pipeline: Built a robust cleaning engine to bypass MoneyControl's formatting. The script automatically handles:

Removal of currency commas and whitespace.

Type conversion from Strings to Numeric floats.

Automated skipping of junk website headers.

Master Database: Initialized fii_dii_master_database.csv. This serves as the "Single Source of Truth" for the analysis.

Incremental Logic: Developed an "Append Engine" that merges daily trading logs while using drop_duplicates logic to ensure data integrity across multiple source months.

📂 Repository Structure
Plaintext
├── data/
│   ├── fii_dii_master_database.csv  <-- Unified history (Jan-Mar)
│   ├── fii_history_2026-02.csv      <-- Original Feb history
│   ├── fii_raw_jan_2026.csv         <-- Jan staging file
│   └── fii_raw_march_2026.csv       <-- March staging file
├── notebooks/
│   └── 03_fii_dii_master.ipynb      <-- Primary Ingestion & Analysis Engine
└── README.md

🚀 Upcoming Milestones (Phase 2: Intelligence)
Day 4: Visualizing Institutional Momentum (FII vs DII Bar Charts).

Day 5-6: Building the "Streak Counter" to identify 3+ days of consecutive FII selling.

Day 7: Calculating the "Volatility Gauge" to flag outlier panic days.