# E-Commerce Data Cleaning & Audit Project

## Overview
This project focuses on auditing, cleaning, and analyzing a messy e-commerce dataset. The goal was to transform raw, inconsistent data into a structured, mathematically sound dataset ready for business intelligence reporting. 

## Tools Used
* **Microsoft Excel:** Used for text standardization (TRIM/PROPER), date formatting (Text-to-Columns), duplicate removal, conditional formatting, and building calculated fields.
* **Excel PivotTables:** Used to generate summary reports and apply business logic filtering.
* **Markdown:** Used for documentation and audit trailing.

## Project Structure
* `raw_data/` - Contains the original, uncleaned dataset.
* `outputs/` 
  * `cleaned_orders.xlsx` - The fully prepped dataset with calculated columns and quality flags.
  * `data_quality_report.xlsx` - A summary of all errors, duplicates, and missing values found.
  * `pivot_summary.xlsx` - 6 Pivot Tables analyzing sales, profits, and margins (excluding cancelled/failed orders).
  * `cleaning_log.md` - A detailed step-by-step audit trail of the cleaning process and business rules applied.

## Key Outcomes
* Standardized text and resolved date formatting conflicts.
* Identified and handled both exact and conflicting duplicate records.
* Built dynamic calculated columns to expose 85 mathematical mismatches in the raw system data.
* Created clean summary reports that accurately reflect true completed sales.

## Key Business Insights
* By applying business rules to filter out cancelled, returned, and failed payment orders, we identified the "True" completed sales performance.
* This audit revealed significant mathematical discrepancies in the raw system export, highlighting the necessity for data validation before reporting.
* New Grand Total for sales   7175634.736
* New Grand Total for profits 2052957.716
