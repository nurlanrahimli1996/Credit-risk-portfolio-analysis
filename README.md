# Credit Risk Portfolio Analysis

## Overview

This project uses the public **Lending Club consumer-loan dataset (2007–2018)** to simulate a practical credit-risk portfolio monitoring and reporting workflow.

The objective is to move from raw loan-level data to a decision-ready view of portfolio quality by combining:

- data validation and cleaning
- credit-risk outcome definition
- portfolio profiling
- borrower-risk segmentation
- loan-characteristic analysis
- vintage analysis
- risk concentration analysis
- advanced visualization
- statistical testing and logistic regression

The project is designed as a business-oriented credit-risk case study rather than a pure machine-learning exercise.

---

## Business Objective

The analysis addresses a central portfolio-management question:

> **Where is credit risk concentrated, and which borrower and loan characteristics are associated with weaker historical performance?**

The workflow was built to reflect the type of analysis used in credit-risk reporting environments, where data quality, reconciliation, portfolio segmentation, trend monitoring and clear communication to decision-makers are as important as statistical modelling.

---

## Dataset

**Source:** Public Lending Club accepted-loan dataset  
**Period:** 2007–2018  
**Unit of analysis:** Individual consumer loan

Key variables used include:

- loan amount
- loan term
- interest rate
- credit grade and sub-grade
- annual income
- debt-to-income ratio (DTI)
- FICO score range
- loan purpose
- origination date
- loan status

Only the variables required for the analysis were loaded into memory to keep the workflow efficient in Google Colab.

---

## Analytical Workflow

### 1. Data Quality and Validation

The raw dataset was reviewed for:

- missing values
- duplicate IDs
- data types
- minimum and maximum values
- percentile distributions
- categorical distributions
- potential anomalies

Rows with missing values in the core analytical variables were removed because missingness was very limited relative to the full dataset.

---

### 2. Defining Credit-Risk Outcomes

Raw loan-status labels were standardized into consistent business categories.

For historical performance analysis, the population was restricted to loans with known final outcomes:

- **Fully Paid**
- **Charged Off**

A binary adverse-outcome indicator was then created:

- `0 = Fully Paid`
- `1 = Charged Off`

This separation prevents active loans from being treated as if their final performance were already known.

---

## Portfolio Baseline

After cleaning and outcome definition, the analysis contained approximately:

- **2.26 million cleaned loan records**
- **1.35 million resolved loans**
- **19.98% historical charge-off rate among resolved loans**

These metrics establish the baseline for the subsequent portfolio analysis.

---

## 3. Portfolio Profiling

The resolved portfolio was profiled using:

- total originated amount
- average and median loan amount
- average interest rate
- average annual income
- average DTI
- average FICO score
- overall charge-off rate

Portfolio performance was also compared across:

- credit grades
- loan terms

---

## 4. Borrower Risk Segmentation

Borrower characteristics were transformed into interpretable analytical bands.

### FICO bands

FICO midpoint values were calculated from the reported lower and upper FICO ranges and grouped into score bands.

The analysis compares:

- portfolio size
- average loan amount
- average pricing
- charge-off rate

across FICO segments.

### DTI bands

Debt-to-income ratios were grouped into:

- `<10`
- `10–20`
- `20–30`
- `30–40`
- `40+`

This allows the analysis to evaluate whether borrowers with heavier debt burdens show systematically different historical performance.

---

## 5. Loan Characteristic Analysis

Credit performance was compared across:

- loan purpose
- loan amount bands
- interest-rate bands
- loan term

The purpose of this section is to distinguish borrower risk from product and pricing characteristics.

---

## 6. Vintage Analysis

Origination dates were converted into yearly and quarterly vintages.

The analysis evaluates how portfolio performance changed across origination periods while recognizing an important limitation:

> Recent vintages have had less time to reach a final outcome than older vintages.

For that reason, more mature vintages were also reviewed separately to reduce incomplete-maturity bias.

---

## 7. Credit-Risk Visualization

Key portfolio patterns were visualized across:

- credit grade
- FICO band
- DTI band
- loan purpose
- origination year

The visual layer is designed to make the analysis easier to communicate to risk managers and senior stakeholders.

---

## 8. Risk Concentration and Interaction Analysis

The analysis moves beyond simple charge-off percentages by combining **risk with portfolio exposure**.

Key views include:

- portfolio share by loan purpose
- charge-off rate by loan purpose
- originated exposure associated with charged-off loans
- exposure-versus-risk bubble chart
- FICO × DTI risk matrix
- pricing versus realized credit risk by grade

This is important because a high-risk segment with little exposure may matter less to the overall portfolio than a moderately risky segment containing a large share of originated balances.

---

## 9. Statistical Analysis

The final stage tests whether the descriptive relationships remain meaningful statistically.

Methods include:

- comparison of borrower characteristics by loan outcome
- Welch's t-tests
- Cohen's d effect sizes
- logistic regression
- odds-ratio interpretation
- multivariate controls
- credit-grade adjustment

Because the dataset is very large, the analysis does not rely on p-values alone. Effect sizes and odds ratios are used to assess practical importance.

A reproducible sample is used for the regression stage to reduce memory pressure in Google Colab.

---

## Tools

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **SciPy**
- **Statsmodels**
- **Google Colab / Jupyter Notebook**

---

## Business Value

This project demonstrates an end-to-end credit-risk analytical workflow:

**raw loan data → validation → outcome definition → portfolio segmentation → risk concentration → visualization → statistical modelling → business interpretation**

The emphasis is on producing analysis that can support:

- portfolio monitoring
- credit-risk reporting
- identification of high-risk segments
- concentration analysis
- management reporting
- decision support

---

## Important Limitations

- The dataset is public Lending Club data and **does not contain U.S. Bank data**.
- Charge-off is used as the adverse historical outcome for resolved loans.
- `charged_off_exposure` represents the original amount associated with charged-off loans and should not be interpreted as accounting loss or loss-given-default.
- Recent vintages may be affected by incomplete loan maturity.
- Analytical FICO, DTI, loan-size and interest-rate bands are project-defined and are not official Lending Club or U.S. Bank thresholds.
- The analysis is observational and should not be interpreted as causal.

---

## Repository Contents

- `Credit_Risk_Portfolio_Analysis.ipynb` — full analysis with code, outputs and visualizations
- `README.md` — project overview and analytical narrative
- Optional executive-summary materials can be added for presentation purposes

---

## Author

**Nurlan Rahimli**

Data Analytics | Business Intelligence | Applied Quantitative Research

