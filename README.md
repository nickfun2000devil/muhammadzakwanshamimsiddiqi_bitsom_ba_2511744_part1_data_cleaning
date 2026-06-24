# E-Commerce Data Cleaning & Audit Project

## 1. Problem Summary
This project focuses on auditing, cleaning, and analyzing a messy, unverified e-commerce transaction dataset. The core business objective was to engineer a reliable, mathematically sound data pipeline by identifying system mismatches, removing duplicate or invalid logs, and isolating true completed transactions to enable accurate financial and operational business intelligence reporting.

## 2. Dataset Description
The source dataset (`raw_orders.xlsx`) contains raw transaction logs detailing customer profiles, geographic regions, item categories, order quantities, base unit pricing, and payment processing states. The uncleaned data suffered from substantial text variations, missing values, broken date configurations, and unaligned financial totals.

## 3. Tools Used
* **Microsoft Excel:** Utilized for data cleaning, text standardization, date parsing via Text-to-Columns, structural filters, and complex logic verification.
* **Excel PivotTables:** Employed to aggregate cleaned fields, generate summary validation matrices, and calculate regional sales distributions.
* **Markdown:** Used to structure documentation, audit trails, and project repository files.

## 4. Data Quality Issues Found & Summary
A comprehensive data quality audit revealed several systemic vulnerabilities across the raw tables:
* **Text Discrepancies:** Massive formatting inconsistencies in text inputs (e.g., mixed casing like "east", "EAST", and "East").
* **Structural Duplicates:** Identical transaction rows logged multiple times, artificially inflating volume.
* **Broken Date Metadata:** Dates stored as non-standard text strings, breaking chronological sorting and chronological analysis.
* **Financial Calculation Anomalies:** Discrepancies between recorded total revenues and calculated values ($Quantity \times Unit \ Price$).
* **Invalid Transaction States:** Inclusions of non-revenue orders containing zero quantities or negative values.

## 5. Cleaning Steps Performed & Business Rules Applied
To resolve the data quality issues, the following systematic cleaning protocol was executed:
1. **Case Standardization:** Applied `=PROPER()` and `=TRIM()` functions across all categorical text variables (Regions, Categories) to eliminate leading spaces and case variations.
2. **Duplicate Eradication:** Utilized Excel's *Remove Duplicates* tool across primary key constraints to isolate unique transaction inputs.
3. **Date Field Normalization:** Extracted and converted text-based date rows using *Text-to-Columns* delimiters and forced the fields into standard `YYYY-MM-DD` formatting.
4. **Calculated Field Audit:** Injected a validation column (`Calculated_Revenue`) using the formula `=Quantity * Unit_Price`. Rows displaying variance against the raw system totals were flagged and reconciled.
5. **Business Logic Filtering:** Isolated true commercial activity by systematically filtering out transactions flagged as cancelled, returned, or failed payment states based on operational data guidelines.

## 6. Summary of Final Pivot Reports
Using the finalized, verified table dataset (`cleaned_orders.xlsx`), a series of foundational validation PivotTables were structured to track core commercial metrics:
* **Sales and Profitability by Region:** Formatted cleanly to outline true baseline transaction volume across geographical segments.
* **Product Category Breakdown:** Outlined margin performance and demand scaling parameters across item lines.

## 7. Key Business Insights
* **Cleaned Performance Baseline:** Following the extraction of data errors and invalid states, the verified True Grand Total for Sales stands at **7,175,634.74** with a True Grand Total for Profits at **2,052,957.72**.
* **Regional Discrepancies:** The structural discrepancies previously identified in the raw export were completely eliminated, providing product managers with clean, trustworthy baseline numbers for localized marketing allocations.

## 8. Assumptions and Limitations
* **Static Context:** The analysis assumes the snapshot accurately reflects a closed 30-day transactional period without trailing accounting adjustments.
* **Currency Uniformity:** All revenue elements are treated as matching currency units without active cross-border conversion adjustments.

## 9. Screenshots Included
Below is the embedded verification evidence showcasing the data structure transformations and the resulting operational summaries:

### Cleaned Funnel Data Preview
![Cleaned Data Preview](cleaned_data_preview.png)

### Final Sales & Profit Pivot Table Summary
![Pivot Summary 1](pivot_summary_1.png)

### Regional Margin Pivot Table Summary
![Pivot Summary 2](pivot_summary_2.png)
