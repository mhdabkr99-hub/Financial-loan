# 🏦 Bank Loan Report — Power BI Dashboard

---

## 📌 Overview

A complete end-to-end **bank loan analytics project** built with Power BI, covering data preparation, DAX measures, SQL validation, and a 3-page interactive dashboard. The dataset contains **38,576 loan records** from fiscal year 2021, sourced from a simulated bank portfolio.

> Built as a portfolio project to demonstrate data analyst skills: data cleaning, KPI design, time intelligence, and storytelling with data.

---

## 📊 Dashboard Pages

| Page | Description |
|------|-------------|
| **Summary** | KPIs, Good vs Bad Loan analysis, Loan Status grid |
| **Overview** | Monthly trends, State map, Term donut, Purpose & Employment charts |
| **Details** | Granular loan table with filters (Grade, State, Good/Bad) |

---

## 🔢 Key Metrics

| Metric | Value |
|--------|-------|
| Total Loan Applications | 38,576 |
| Total Funded Amount | $435.8M |
| Total Amount Received | $473.1M |
| Avg Interest Rate | 12.05% |
| Avg DTI | 13.33% |
| Good Loan Rate | 86.2% |
| Bad Loan Rate (Charged Off) | 13.8% |

---

## 🛠️ Tech Stack

- **Power BI Desktop** — Dashboard & visualizations
- **Power Query (M)** — Data cleaning & column typing (`en-US` locale fix)
- **DAX** — 20+ measures: KPIs, MTD, PMTD, MoM, Good/Bad Loan
- **MS SQL Server** — Query validation
- **Custom JSON Theme** — Navy blue color palette

---

## 📁 Repository Structure

```
bank-loan-report/
│
├── data/
│   └── financial_loan.csv        # Raw dataset (38,576 rows × 24 cols)
│
├── powerbi/
│   └── bank_loan_report.pbix     # Power BI report file
│
├── theme/
│   └── BankLoan_Theme.json       # Custom Power BI theme
│
├── sql/
│   └── queries.sql               # All SQL validation queries
│
└── README.md
```

---

## ⚡ DAX Highlights

```dax
-- MTD with time intelligence
MTD Loan Applications =
    TOTALMTD(COUNT(financial_loan[id]), financial_loan[issue_date])

-- MoM variation
MoM Loan Applications =
    DIVIDE([MTD Loan Applications] - [PMTD Loan Applications],
           [PMTD Loan Applications], 0)

-- Good Loan %
Good Loan Percentage =
    DIVIDE(
        CALCULATE(COUNT(financial_loan[id]),
            financial_loan[loan_status] = "Fully Paid"
            || financial_loan[loan_status] = "Current"),
        COUNT(financial_loan[id]), 0)
```

---

## 📌 Dataset Columns

`id` · `address_state` · `application_type` · `emp_length` · `emp_title` · `grade` · `home_ownership` · `issue_date` · `loan_status` · `purpose` · `sub_grade` · `term` · `verification_status` · `annual_income` · `dti` · `installment` · `int_rate` · `loan_amount` · `total_acc` · `total_payment`

---

## 🚀 How to Use

1. Clone the repository
2. Open `bank_loan_report.pbix` in Power BI Desktop
3. Apply the theme: **View → Themes → Browse → BankLoan_Theme.json**
4. If data doesn't load, re-point the source to `data/financial_loan.csv`

---

## 👤 Mouhammad Aboubakar

Portfolio project — Data Analytics · Power BI · SQL · DAX
