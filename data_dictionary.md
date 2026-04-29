# Data Dictionary — Indian Banking Transactions Dataset

**Dataset:** indian_banking_transactions.csv  
**Records:** 550,000 transactions | **Period:** 2019-01-01 to 2024-01-01  
**Source:** ApexPlanet Software Pvt. Ltd. Internship — Task 1

---

| # | Column Name | Data Type | Description | Business Relevance |
|---|-------------|-----------|-------------|-------------------|
| 1 | transaction_id | String (PK) | Unique identifier for each transaction (e.g., TXN000000001) | Primary key for transaction tracing and deduplication |
| 2 | customer_id | String (FK) | Unique customer identifier (e.g., CUST015796) | Links transactions to customer profiles for lifetime value analysis |
| 3 | transaction_date | String → Date | Date of transaction (YYYY-MM-DD format) | Enables time-series analysis, trend detection, seasonality |
| 4 | transaction_time | String → Time | Time of transaction (HH:MM format) | Used for peak-hour analysis and fraud pattern detection |
| 5 | account_type | Categorical | Type of bank account: Savings, Current, Salary, Fixed Deposit, NRI | Segmentation of customers by account product |
| 6 | transaction_type | Categorical | Payment method: UPI, POS, Net_Banking, NEFT, Credit_Card, Cheque, ATM_Withdrawal, IMPS, RTGS, Auto_Debit | Channel adoption and digital payment trend analysis |
| 7 | transaction_amount | Float (INR) | Monetary value of transaction (₹2.40 – ₹10,000,000) | Core KPI for revenue, spend analysis, and outlier detection |
| 8 | transaction_direction | Categorical | Debit or Credit — direction of money flow | Cash flow and net position analysis per customer |
| 9 | account_balance | Float (INR) | Account balance after transaction (₹500 – ₹5,000,000) | Liquidity assessment and financial health indicator |
| 10 | merchant_category | Categorical | Category of spend: Food & Dining, Travel, Healthcare, Education, Utilities, Government, Investment, Real Estate, E-Commerce, Retail | Spending pattern and category-wise revenue analysis |
| 11 | state | Categorical | Indian state where transaction occurred (10 states) | Geographic distribution and regional performance analysis |
| 12 | credit_score | Integer (300–899) | Customer credit score at time of transaction | Credit risk segmentation and loan eligibility assessment |
| 13 | has_loan | Binary (0/1) | Whether customer has an active loan (0=No, 1=Yes) | Loan penetration rate and cross-sell opportunity identification |
| 14 | loan_type | Categorical (Nullable) | Type of loan: Personal, Home, Auto, Business, Education, Gold; NULL if no loan | Loan product mix analysis; 68.6% customers have no loan |
| 15 | emi_amount | Float (INR) | Monthly EMI amount (0 if no loan) | Loan repayment burden and default risk assessment |
| 16 | transaction_status | Categorical | Outcome: Success, Pending, Failed, Reversed | Transaction success rate and failure root-cause analysis |
| 17 | channel | Categorical | Banking channel: Branch, Mobile_App, Web, ATM, API, POS_Terminal | Digital adoption rate and channel preference analysis |
| 18 | kyc_status | Categorical | KYC compliance: Verified, Expired, Pending | Regulatory compliance monitoring |
| 19 | is_fraud | Binary (0/1) | Fraud label: 1=Fraudulent, 0=Legitimate (0.886% fraud rate) | Fraud detection model target variable |
| 20 | transaction_hour | Integer (0–23) | Hour of transaction extracted from transaction_time | Peak-hour analysis, night-time fraud pattern detection |

---

## Summary Statistics

| Field | Min | Max | Mean | Median |
|-------|-----|-----|------|--------|
| transaction_amount | ₹2.40 | ₹10,000,000 | ₹29,907 | ₹2,036 |
| account_balance | ₹500 | ₹5,000,000 | ₹84,550 | ₹36,423 |
| credit_score | 300 | 899 | 600 | 600 |
| emi_amount | ₹0 | ₹153,326 | ₹2,366 | ₹0 |

## Data Quality Notes
- **Missing Values:** `loan_type` has 377,134 NULLs (68.6%) — expected, as customers without loans have no loan type
- **Duplicates:** 0 duplicate records found
- **Outliers:** `transaction_amount` has extreme values up to ₹10M (RTGS/large transfers expected)
- **Fraud Rate:** 0.886% (4,873 fraudulent transactions) — class imbalance noted
