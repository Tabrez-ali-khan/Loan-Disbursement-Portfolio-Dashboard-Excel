# Loan Disbursement Portfolio Dashboard | Microsoft Excel

![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![Pivot Tables](https://img.shields.io/badge/Pivot_Tables-1F4E79?style=for-the-badge)
![Slicers](https://img.shields.io/badge/Slicers_%26_Timelines-F2C811?style=for-the-badge)
![KPI](https://img.shields.io/badge/KPI_Development-ED7D31?style=for-the-badge)

An interactive **Excel** dashboard for a loan portfolio of **500 loans (₹121.2M disbursed)**, built with Pivot Tables, slicers and a timeline. It tracks disbursement, default rate, credit score, EMI and recoveries, and asks one question: **does credit score alone explain which loans default?**

<img width="1876" height="1002" alt="Image" src="https://github.com/user-attachments/assets/65a8944d-2ec2-4ed3-aeac-bf82ec8fdebe" />

> **About the data:** this project uses a **randomly generated (synthetic) dataset** created for practice. It does not represent a real lender or real customers. Loan statuses split almost evenly (about 25% each), which is typical of generated data, so the findings illustrate the method and are not real lending results.

---

## Project at a Glance

| Metric | Value |
| --- | --- |
| Loan records | 500 |
| Disbursement period | 7 Jan 2022 – 28 Dec 2023 |
| Total disbursed | ₹121.2M (average loan ₹242K) |
| Default rate | 24.80% (124 of 500 loans) |
| Total recovered | ₹14.4M, which is 46.9% of defaulted loan value |
| Average credit score | 573.4 |
| Average EMI | ₹32,795 |
| Average interest rate / tenure | 24.2% / 13.3 months |
| Cities / loan purposes | 5 cities, 5 purposes |
| Employment types | Salaried and Self-Employed |

---

## Business Questions

1. How much has been disbursed, and how does it change month by month?
2. How are loans split between Active, Closed, Defaulted and Restructured?
3. Which cities and loan purposes carry the most loans and the most defaults?
4. How much of the defaulted value has been recovered?
5. Does credit score, employment type or loan tenure separate defaulting loans from the rest?

---

## Tools

Microsoft Excel · Pivot Tables · Pivot Charts · Slicers · Timeline · KPI measures

---

## Dataset

The source data is [`data/Loan_Data.csv`][Loan_Disbursement_Dashboard.xlsx](https://github.com/user-attachments/files/33027288/Loan_Disbursement_Dashboard.xlsx), one row per loan (500 rows). The same data sits in the **Raw Data** sheet of the Excel file.

| Column | Description |
| --- | --- |
| Loan_ID, Customer_ID | Identifiers |
| Age, Gender, City | Customer attributes (5 cities: Bangalore, Chennai, Delhi, Hyderabad, Mumbai) |
| Employment_Type, Monthly_Income | Salaried or Self-Employed, and monthly income |
| Loan_Amount, Loan_Tenure_Months, Interest_Rate, EMI_Amount | Loan terms (tenure of 3, 6, 12, 18 or 24 months) |
| Loan_Purpose | Business, Education, Medical, Shopping or Travel |
| Loan_Status | Active, Closed, Defaulted or Restructured |
| Disbursement_Date, Closure_Date, Days_to_Close | Dates (closure fields are blank for 252 loans) |
| Credit_Score | Ranges from 300 to 850 |
| DPD_30 | Whether the loan went 30+ days past due |
| Recovery_Amount | Amount recovered (recorded only for defaulted loans) |

---

## Approach

### 1. KPI framework
The **KPI** sheet holds the portfolio measures. Each one is calculated with a formula and cross-checked against a pivot table value.

| KPI | Definition |
| --- | --- |
| Total Disbursement | Sum of `Loan_Amount` |
| Default Rate | Defaulted loans ÷ total loans |
| Avg Credit Score | Average of `Credit_Score` |
| Avg EMI | Average of `EMI_Amount` |
| Total Recovery | Sum of `Recovery_Amount` |
| Recovery Rate | Total recovery ÷ loan amount of defaulted loans |
| MTD and MoM | December compared with November, matched by month name across both years: (MTD − PMTD) ÷ PMTD |

### 2. Pivot tables and charts
- Built pivot tables for status mix, loan purpose, city, employment type by tenure, and monthly disbursement
- Turned them into pivot charts on a **Charts** sheet
- Arranged the KPI cards and charts on the **DashBoard Layout** sheet

### 3. Interactivity
- A **Disbursement_Date timeline** plus slicers for **Loan_Status, Loan_Purpose and City**
- Every chart and KPI card responds to the same filters, so any slice of the portfolio can be compared instantly

---

## Dashboard

| Element | What it shows |
| --- | --- |
| KPI cards | Total loans, disbursement, default rate, average credit score, average EMI and recovery, each with MTD and month-on-month change |
| Monthly Disbursement Trend | Disbursement by month, January 2022 to December 2023 |
| Loan Status Mix | Donut chart of Active, Closed, Defaulted and Restructured loans |
| Loan Purpose Analysis | Disbursement by purpose |
| Loans by City | Loan count by city. Set the Loan_Status slicer to *Defaulted* to see defaulted loans per city |
| Employment Type vs Loan Tenure | Disbursed amount by employment type and tenure (3, 6, 12, 18, 24 months) |

---

## Key Insights

**Portfolio**
- **₹121.2M disbursed across 500 loans.** Disbursement grew from ₹54.0M in 2022 (234 loans) to ₹67.2M in 2023 (266 loans), up about 24%.
- **The status mix is almost even:** Active 128, Closed 127, Defaulted 124 and Restructured 121.
- **Business is the largest purpose** at ₹27.5M, followed by Education (₹26.1M), Travel (₹24.3M), Medical (₹23.3M) and Shopping (₹20.0M).
- **The MTD cards compare December with November** (both years combined): 36 vs 51 loans (−29.4%) and ₹7.8M vs ₹12.5M disbursed (−37.5%). For December 2023 alone, the figures are 21 loans and ₹4.4M against 28 loans and ₹6.7M in November 2023.

**Defaults and recovery**
- **₹14.4M was recovered from ₹30.8M of defaulted loans (46.9%),** leaving about ₹16.3M unrecovered.
- Every loan that defaulted or was restructured had gone 30+ days past due.

**Does credit score explain default? Not on its own.**

| Group | Default rate |
| --- | --- |
| Credit score 300–500 / 501–600 / 601–700 / 701–900 | 25.0% / 22.1% / 21.0% / 29.5% |
| Salaried / Self-Employed | 27.3% / 22.4% |
| Tenure 3 / 6 / 12 / 18 / 24 months | 19.8% / 24.0% / 23.2% / 26.3% / 29.1% |
| Bangalore / Mumbai / Chennai / Delhi / Hyderabad | 14.8% / 22.5% / 26.0% / 30.2% / 30.9% |

- Default rate does not fall as credit score rises, and the **701–900 band has the highest rate (29.5%)**.
- Longer tenures default somewhat more often, rising from about 20% at 3 months to 29% at 24 months.
- **City shows the widest gap**, with Delhi and Hyderabad above 30% and Bangalore at 14.8%.
- A chi-square check on the raw data found no statistically significant link between default and credit score band (p = 0.44), employment type (p = 0.23) or tenure (p = 0.64). City was borderline (p = 0.046). With 500 synthetic loans, treat these as pointers, not proof.

---

## Recommendations

- **Do not approve on credit score alone.** In this data it does not separate defaulting loans, so add other signals such as city, tenure and repayment history.
- **Review lending in Delhi and Hyderabad,** where about 30% of loans default, against Bangalore at about 15%.
- **Watch the 18 and 24 month tenures,** which show the highest default rates.
- **Focus collections on the remaining ₹16.3M** of defaulted value, since recovery stands at 46.9%.
- **Investigate the December 2023 drop** (21 loans, ₹4.4M, against ₹6.7M in November) before treating it as a trend.

---

## Limitations

- The data is synthetic, so the findings illustrate the method and are not real business results.
- 500 loans is a small sample, and the differences in default rate between groups are mostly not statistically significant.
- Recoveries are recorded only on defaulted loans, so recovery rate is measured against defaulted value only.
- The MTD and MoM cards match months by name without the year, so December combines 2022 and 2023.
- The dashboard has no predictive model. It compares default rates across groups with pivot tables.
- Interest rates (12% to 36%) and the near-even status split are typical of generated data, so no real lending conclusions should be drawn.

---

## Repository Structure

```
Loan-Disbursement-Portfolio-Dashboard-Excel/
├── README.md
├── data/
│   └── Loan_Data.csv
├── excel/
│   └── Loan_Disbursement_Dashboard.xlsx
└── screenshots/
    └── 01_Loan_dashboard_overview.png
```

## How to Use

1. Download `Loan_Disbursement_Dashboard.xlsx` from the `excel/` folder and open it in **Microsoft Excel** (best viewed in desktop Excel so the slicers and timeline work fully).
2. Go to the **DashBoard Layout** sheet and use the timeline and slicers to filter by date, status, purpose and city.
3. Open the **Pivot Tables** and **KPI** sheets to see the numbers behind each chart and card.

---

## Author

**Mohammed Tabrez Ali Khan** · Data Analyst
Riyadh, Saudi Arabia · [LinkedIn](https://www.linkedin.com/in/md-tabrez-ali-khan) · mdtabrezalik@gmail.com
