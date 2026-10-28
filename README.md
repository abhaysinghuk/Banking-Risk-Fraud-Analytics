# Banking-Risk-Fraud-Analytics

Bank Transaction Fraud Risk Analysis
Project Overview

This project focuses on analyzing banking transactions to identify unusual activity and prioritize potentially risky transactions for further investigation. It combines Python-based data analysis, PostgreSQL queries, Excel reporting, and Power BI visualization to build an end-to-end fraud risk analysis workflow.

Since the source dataset does not contain confirmed fraud labels, a statistical rule-based scoring method is used to highlight transactions with unusual characteristics. The results are exploratory risk indicators rather than verified fraud classifications.

Business Objective

Financial institutions need reliable ways to review large volumes of transactions, identify irregular patterns, and investigate potential risks. Manual reviews can be time-consuming, especially when suspicious activity is spread across multiple transactions or accounts.

The objective of this project is to:

Identify transactions with unusual financial or behavioral characteristics.
Analyze transaction patterns across accounts, merchants, locations, and time periods.
Develop a statistical method for flagging potential risk indicators.
Compare findings across analytical tools to maintain consistent reporting.
Present actionable observations through an interactive dashboard.
Project Highlights
Analyzed and processed 2,512 banking transactions using Python and Pandas.
Developed an IQR-based statistical scoring method using transaction amount, login attempts, and transaction duration.
Flagged 230 transactions (9.16%) for further review based on the implemented risk rules.
Compared headline results across Python, PostgreSQL, Excel, and Power BI.
Built an interactive dashboard containing key metrics, geographic comparisons, monthly trends, and account-level risk summaries.
Investigated transaction-volume bias and used rate-based comparisons to improve geographic analysis.
Technology Stack
Technology	Application
Python	Data preparation, feature engineering, exploratory analysis, and statistical scoring
Pandas	Data manipulation, cleaning, and aggregation
PostgreSQL	Transaction queries, account ranking, and merchant-level analysis
Microsoft Excel	Pivot tables, KPI calculations, and conditional formatting
Power BI	Interactive reporting, visual analysis, and DAX measures
Analytical Workflow
1. Data Preparation
Imported the original banking transaction dataset.
Checked data types, missing values, and consistency of transaction fields.
Converted date and time fields into usable formats.
Created additional features, including transaction hour and day of the week.
Exported a cleaned dataset for subsequent analysis.
2. Statistical Risk Scoring

Implemented an Interquartile Range (IQR)-based approach to identify observations outside expected data ranges.

The scoring method examines three transaction characteristics:

Transaction amount
Number of login attempts
Transaction duration

Transactions triggering one or more rules are flagged for further review. The number of triggered signals is also examined to distinguish transactions with multiple unusual characteristics.

Important: These flags represent statistical anomalies, not confirmed fraudulent transactions. The method does not establish fraud probability or validate actual fraud outcomes.

3. Exploratory Data Analysis

Analyzed transaction distributions and compared suspicious activity across different dimensions, including geographic location, accounts, merchants, and available time periods.

During the analysis, raw suspicious-transaction counts were found to be affected by differences in transaction volume. Rate-normalized comparisons were therefore used to support more meaningful geographic comparisons.

4. SQL-Based Investigation

Used PostgreSQL to investigate transaction patterns and summarize potentially risky activity.

The SQL analysis includes:

Aggregating flagged transactions by account and merchant.
Ranking accounts according to accumulated risk indicators.
Comparing suspicious activity across geographic groups.
Summarizing transaction counts and relevant metrics.
Supporting further investigation through filtered query results.
5. Excel Reporting

Created an Excel-based reporting layer using pivot tables, formulas, and conditional formatting.

The workbook supports KPI summaries, comparisons of transaction patterns, and identification of records requiring additional review.

6. Power BI Dashboard

Developed an interactive dashboard to make the analysis easier to explore and communicate.

Dashboard components include:

KPI cards for transaction volume and flagged activity.
Geographic comparisons of suspicious transaction rates.
Monthly transaction trend visualizations.
Account-level summaries highlighting repeated risk indicators.
Interactive filters and drill-down analysis.
Key Findings
1. Transactions Requiring Review

A total of 230 out of 2,512 transactions (9.16%) triggered at least one implemented risk rule. Five transactions triggered two signals simultaneously.

These results describe the behavior of the statistical scoring rules and should not be interpreted as a confirmed fraud rate.

2. Geographic Differences

Austin, Fort Worth, and San Diego showed suspicious activity rates above the overall dataset baseline in this analysis. Rate-based comparisons helped reduce the distortion that can occur when locations have different transaction volumes.

These findings are specific to the dataset and do not establish that the locations have higher real-world fraud rates.

3. Time-Based Patterns

Time-of-day was not a strong differentiator in the available data. The dataset covers only a limited portion of the day, so broader conclusions about transaction timing would require more comprehensive observations.

4. Repeated Account-Level Indicators

Some accounts accumulated risk indicators across multiple transactions, even when individual transactions did not exhibit extreme values.

This suggests that account-level monitoring may complement transaction-level anomaly screening.

Business Recommendations

Based on the exploratory findings, the following improvements could strengthen a practical risk monitoring workflow:

Prioritize transactions that trigger multiple independent risk indicators.
Review accounts with repeated unusual activity across transactions.
Compare geographic suspicious rates alongside transaction volumes.
Reassess risk thresholds to reduce false positives caused by low-variance features.
Introduce labeled transaction data to evaluate detection precision and recall.
Monitor data quality and scoring performance as new transactions become available.
Repository Structure
text
bank-transaction-risk-analysis/
│
├── data/
│   ├── bank_transactions_data_2.csv
│   └── fraud_data_cleaned.csv
│
├── python/
│   ├── phase2_explore.py
│   ├── phase3_cleaning.py
│   └── phase4_eda.py
│
├── sql/
│   └── fraud_analysis_queries.sql
│
├── excel/
│   └── fraud_data_cleaned.xlsx
│
├── powerbi/
│   └── dashboard.pbix
│
├── docs/
│   ├── phase1_project_planning.md
│   ├── phase8_insights.md
│   └── phase9_recommendations.md
│
└── README.md

Dataset

The project uses the publicly available Bank Transaction Dataset for Fraud Detection from Kaggle:

https://www.kaggle.com/datasets/valakhorasani/bank-transaction-dataset-for-fraud-detection

Refer to the original dataset page for source details and applicable usage terms.

Limitations
The source dataset does not provide confirmed fraud labels, so the scoring method identifies unusual observations rather than verified fraud.
The login-attempt feature has limited variance, which can make its IQR-based rule overly sensitive.
The available time coverage is limited, restricting the reliability of time-of-day comparisons.
Statistical thresholds may generate false positives and require further validation.
The reported results describe this dataset and should not be generalized to actual banking operations without additional evidence.
Future Enhancements
Evaluate alternative anomaly detection methods, such as Isolation Forest.
Tune scoring thresholds and investigate false-positive behavior.
Incorporate labeled data to measure precision, recall, and other detection metrics.
Add automated data-quality checks and repeatable reporting.
Extend monitoring to account-level transaction sequences and changing activity patterns.
Conclusion

This project demonstrates an end-to-end approach to transaction data preparation, statistical risk screening, SQL-based investigation, reporting, and dashboard development. It provides a practical foundation for exploring risk indicators and communicating analytical findings while recognizing the limitations of unlabeled data.

Skills demonstrated: Python, Pandas, PostgreSQL, Excel, Power BI, Data Cleaning, Exploratory Data Analysis, Statistical Outlier Detection, Transaction Monitoring, Risk Analysis, KPI Reporting, and Data Visualization.
