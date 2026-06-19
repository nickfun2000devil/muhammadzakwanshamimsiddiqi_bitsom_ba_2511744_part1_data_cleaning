# Data Cleaning Log

## 1. List of Issues Found
* Inconsistent casing, trailing spaces, and extra spaces in text fields (Category, City, State, etc.).
* Invalid date formats mixing American (MM/DD/YYYY) and European (DD/MM/YYYY) standards, causing `#VALUE!` errors.
* 20 Exact duplicate records.
* 24 Conflicting duplicate records (same order_id, different data).
* Missing values in `region` (25) and `ship_mode` (21).
* Illogical discounts (negative values or values over 100%).
* Time-travel shipping records (Ship dates logged before Order dates).
* 85 Calculation mismatches between reported sales/profit and actual calculated math.

## 2. Cleaning Actions Performed
* Used `=TRIM(PROPER())` helper columns to standardize all text fields and pasted values over the originals.
* Used Excel's "Text to Columns" wizard with the MDY setting to force Excel to recognize American date strings as valid dates.
* Used the "Remove Duplicates" tool on the entire dataset to eliminate 100% exact row matches.
* Built calculated columns to dynamically check math (`calculated_sales`, `calculated_profit`).
* Standardized discount values by converting percentage formats to decimal values to ensure mathematical accuracy in sales and profit calculations.

## 3. Business Rules Applied
* Blank regions and ship modes were hardcoded as "Unknown".
* Invalid discounts (<0 or >1) were forced to 0 in the new `cleaned_discount` column.
* Cancelled and Failed orders were filtered out of final Completed Sales summaries in the Pivot reporting.

## 4. Assumptions Made
* Assumed the system's underlying mathematical logic (Sales = Qty * Price * (1 - Discount)) was the source of truth, rather than the hardcoded numbers in the raw export.
* Assumed missing discount data meant no discount was given (0%).

## 5. Records Removed
* 20 exact duplicate rows were permanently removed.

## 6. Records Flagged
* A dedicated `data_quality_flag` column was created. 
* Flagged 24 Conflicting Duplicates, 25 Missing Regions, 21 Missing Ship Modes, 14 Invalid Discounts, and 193 Invalid Shipping Records. 
* A dedicated `mismatch_flag` column flagged 85 math errors.

## 7. Limitations of the Cleaning Process
* Conflicting duplicates were flagged but not deleted. Without accessing the original CRM/database, it is impossible to know which of the conflicting rows contains the true data.
* Changing invalid discounts to 0 might artificially inflate the calculated sales figures if a valid discount was simply typed incorrectly (e.g., typing -0.15 instead of 0.15).