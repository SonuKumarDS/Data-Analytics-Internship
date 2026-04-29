# Indian Banking Data Analytics — Internship Portfolio
## ApexPlanet Software Pvt. Ltd. | 60-Day Data Analytics Internship

---

## Dataset Overview
**File:** `indian_banking_transactions.csv`  
**Records:** 550,000 transactions | **Features:** 20 raw → 32 after engineering  
**Period:** January 2019 – January 2024  
**Domain:** Indian Banking & Financial Services

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
