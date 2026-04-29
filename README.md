# Indian Banking Data Analytics — Internship Portfolio
## ApexPlanet Software Pvt. Ltd. | 60-Day Data Analytics Internship

---

## Dataset Overview
**File:** `indian_banking_transactions.csv`  
**Records:** 550,000 transactions | **Features:** 20 raw → 32 after engineering  
**Period:** January 2019 – January 2024  
**Domain:** Indian Banking & Financial Services

---

## Task Summary

| Task | Title | Duration | Status |
|------|-------|----------|--------|
| Task 1 | Data Immersion & Wrangling | 10 Days | ✅ Complete |
| Task 2 | EDA & Business Intelligence | 14 Days | ✅ Complete |
| Task 3 | Deep-Dive & Interactive Dashboarding | 12 Days | ✅ Complete |
| Task 4 | Data Storytelling & Statistical Validation | 16 Days | ✅ Complete |
| Task 5 | Capstone Integration & Portfolio Finalization | 8 Days | ✅ Complete |

---

## TASK 1 — Data Immersion & Wrangling

### Objective
Acquire, clean, and prepare the banking dataset for analysis.

### Data Quality Assessment Results
| Issue | Finding | Resolution |
|-------|---------|------------|
| Missing Values | `loan_type`: 377,134 NULLs (68.6%) | Filled with "No_Loan" |
| Duplicates | 0 duplicate rows | No action needed |
| Outliers | 88,976 transaction_amount outliers (16.18%) | Flagged with `is_amount_outlier` column |
| Date Format | String format YYYY-MM-DD | Parsed to datetime |
| EMI Consistency | Some has_loan=0 rows had emi_amount>0 | Corrected to 0 |

### Feature Engineering (12 new columns)
- `year`, `month`, `month_name`, `quarter`, `day_of_week` — temporal decomposition
- `time_of_day` — Morning / Afternoon / Evening / Night bins
- `credit_score_band` — Poor / Fair / Good / Very Good / Excellent
- `amount_category` — Micro / Small / Medium / Large / Very Large
- `net_amount` — signed amount (negative for debits)
- `is_weekend`, `is_high_value`, `is_amount_outlier` — binary flags

### Deliverables
- `data_dictionary.md` — 20-field data dictionary
- `data_cleaning.py` — Complete cleaning script
- `cleaned_dataset.csv` — 550,000 × 32 analysis-ready dataset

---

## TASK 2 — EDA & Business Intelligence

### Objective
Uncover patterns and answer 7 business questions via SQL.

### Key Descriptive Statistics
| Metric | Value |
|--------|-------|
| Avg Transaction Amount | ₹29,907 |
| Avg Account Balance | ₹84,550 |
| Avg Credit Score | 600 |
| Transaction Success Rate | 92.04% |
| Fraud Rate | 0.886% |

### SQL Business Questions & Key Findings
1. **Top Merchant Categories by Revenue** → Retail (₹1.09B) > E-Commerce (₹892M) > Food & Dining (₹867M)
2. **Monthly Transaction Trends** → Stable ~9,000-9,500 transactions/month
3. **State-wise Fraud Rates** → UP (0.948%) > West Bengal (0.940%) > Karnataka (0.914%)
4. **Channel Success Rates** → ATM 92.09% ≈ Web 92.09% ≈ Mobile 92.06%
5. **Fraud by Transaction Type** → Distributed uniformly (~0.886%) across types
6. **Credit Score vs Financial Metrics** → Excellent-band customers: 2x higher avg balance
7. **Loan Penetration by Account Type** → All types ~35% penetration

### Visualizations
- `fig1_univariate.png` — Distribution histograms & categorical bar charts
- `fig2_multivariate.png` — Monthly trends, state performance, fraud analysis, credit bands
- `eda_sql_results.xlsx` — All 7 SQL query results

---

## TASK 3 — Deep-Dive Analysis & Interactive Dashboarding

### Objective
Perform customer segmentation and fraud deep-dive; build KPI dashboard.

### Core KPIs Defined
| KPI | Formula | Value |
|-----|---------|-------|
| Transaction Success Rate | Success Txns / Total Txns | 92.04% |
| Fraud Detection Rate | Fraud Txns / Total Txns | 0.886% |
| Average Transaction Value | Sum(Amount) / Count | ₹29,907 |
| Loan Penetration Rate | Customers with Loan / Total | 34.96% |
| Digital Channel Share | Digital Txns / Total Txns | ~67% |

### Customer Segmentation (K-Means, k=4)
| Segment | Count | Avg Total Spend | Avg Balance |
|---------|-------|----------------|-------------|
| High-Value Spenders | 3,058 (3.8%) | ₹15.7L | ₹79,505 |
| Affluent Savers | 4,744 (5.9%) | ₹1.46L | ₹2,81,238 |
| Active Transactors | 34,935 (43.7%) | ₹1.98L | ₹76,647 |
| Occasional Users | 37,179 (46.5%) | ₹1.09L | ₹66,752 |

### Fraud Deep-Dive Findings
- Total fraud cases: **4,873** (0.886% rate)
- Avg fraud transaction: ₹31,294 vs legit ₹29,881
- Night-time fraud pattern: Not statistically elevated (see Task 4)
- Geographic hotspot: **UP and West Bengal** — highest fraud rates

### Deliverables
- `chart1_segmentation.png` — Cluster scatter + pie
- `chart2_fraud_deepdive.png` — 5-panel fraud analysis
- `chart3_kpi_dashboard.png` — Full KPI dashboard
- `customer_segments.csv` — 79,916 customer profiles with segments

---

## TASK 4 — Data Storytelling & Statistical Validation

### The Data Story
**Setting:** Indian banking sector, 2019–2024, 550K transactions across 10 states  
**Objective:** Understand transaction patterns, fraud, and customer behavior to drive business decisions  
**Conclusion:** Maharashtra leads in volume; digital adoption is strong; high-CS customers are prime targets for premium products; fraud requires geographic-specific interventions

### Hypothesis Tests

#### H1: Digital channels have higher average transaction amounts than physical
- **Test:** Welch's Independent T-test
- **Result:** T=1.438, p=0.150 → **FAIL TO REJECT H0**
- **Business Insight:** Digital and physical channel customers transact similar amounts — no channel premium exists

#### H2: Night-time fraud rate is higher than daytime
- **Test:** Chi-squared test for proportions
- **Result:** Chi2=0.484, p=0.487 → **FAIL TO REJECT H0**
- **Business Insight:** Fraud is uniformly distributed across hours — 24/7 monitoring is needed, not just night-time alerts

#### H3: High credit score customers (>700) have higher account balances
- **Test:** One-tailed Welch's T-test
- **Result:** T=1.938, p=0.026 → **REJECT H0 ✅ (Statistically Significant)**
- **Business Insight:** High-CS customers hold significantly more balance — validate premium product targeting
- **95% CI:** High-CS customers hold ₹958 more avg balance (small but significant at scale)

### Deliverables
- `chart1_data_story.png` — Full narrative visualization with hypothesis results

---

## TASK 5 — Capstone Integration & Portfolio Finalization

### Portfolio Structure
```
DataAnalytics-Internship-Portfolio/
├── README.md                          ← This file (master overview)
├── task1/
│   ├── data_dictionary.md
│   ├── data_cleaning.py
│   └── cleaned_dataset.csv
├── task2/
│   ├── eda_analysis.py
│   ├── eda_sql_results.xlsx
│   ├── fig1_univariate.png
│   └── fig2_multivariate.png
├── task3/
│   ├── deep_dive.py
│   ├── chart1_segmentation.png
│   ├── chart2_fraud_deepdive.png
│   ├── chart3_kpi_dashboard.png
│   └── customer_segments.csv
├── task4/
│   └── chart1_data_story.png
└── task5/
    └── chart1_capstone_portfolio.png
```

### Technical Skills Demonstrated
- **Python:** Pandas, NumPy, Matplotlib, Seaborn, SciKit-Learn, SciPy
- **SQL:** SQLite, aggregations, window logic, joins
- **Statistics:** T-tests, Chi-squared, confidence intervals, p-values
- **ML:** K-Means clustering, StandardScaler, feature engineering
- **Data Storytelling:** Multi-panel dashboards, KPI design, business narrative

### Key Business Findings
1. **Maharashtra is the #1 market** — ₹2.98B volume, 18% market share
2. **Fraud is uniformly distributed** — no single channel/hour hotspot; requires broad prevention strategy
3. **65% customers are untapped** for loan products — significant cross-sell opportunity
4. **High credit score customers statistically validated** to hold higher balances — prime premium banking targets
5. **Digital channels dominant** at 67% of transactions — continued mobile-first investment is justified

---

*Completed as part of ApexPlanet Software Pvt. Ltd. 60-Day Data Analytics Internship Program*  
*Contact: apexplanetgaya@gmail.com | www.apexplanet.in*
