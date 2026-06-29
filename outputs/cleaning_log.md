# Data Cleaning Log

 

## Overview

 

This document describes the data cleaning and preparation steps performed on the raw dataset (raw_orders.xlsx).

 

The objective was to improve data quality by handling missing values, removing inconsistencies, and preparing the dataset for reliable analysis and reporting.

 

---

 

## 1. Duplicate Handling

 

- Checked duplicate records using `order_id` 

- Exact duplicate rows were removed 

- Records with duplicate order IDs but inconsistent values were **flagged instead of deleted** 

- This approach maintains data transparency and avoids incorrect data loss 

 

---

 

## 2. Missing Data Handling

 

- Checked missing values in key fields:

  - region 

  - ship_mode 

  - order_date 

  - ship_date 

 

- Handling approach:

  - Missing `region` and `ship_mode` → replaced with **"Unknown"** 

  - Missing `discount` → treated as 0 only when other values were valid 

  - Missing or invalid dates → **flagged** for data quality issues 

 

---

 

## 3. Data Standardization

 

- Removed extra spaces using **TRIM** 

- Standardized text format using **PROPER** 

- Ensured consistency across:

  - customer_name 

  - region 

  - category 

  - sub_category 

  - ship_mode 

  - order_status 

 

This ensures uniform formatting across the dataset.

 

---

 

## 4. Date Cleaning

 

- Converted `order_date` and `ship_date` into proper Excel date format 

- Handled inconsistent formats using conversion methods 

- Identified invalid date cases 

 

- Special validation:

  - Records where **ship_date < order_date** were flagged as invalid 

 

---

 

## 5. Discount and Value Validation

 

- Missing discount values handled as defined in business rules 

- Negative discount values were flagged as invalid 

- Discount values outside acceptable range were flagged 

 

---

 

## 6. Sales and Profit Validation

 

- Recalculated values:

  - Sales = quantity × unit_price × (1 − discount) 

  - Profit = sales − cost 

 

- Compared calculated and original values 

- Mismatches were flagged for validation 

 

---

 

## 7. Derived Fields Created

 

Additional fields were created to support analysis:

 

- cleaned_discount 

- calculated_sales 

- calculated_profit 

- profit_margin 

- shipping_delay_days 

- order_month 

- order_year 

 

These fields help in reporting and detecting inconsistencies.

 

---

 

## 8. Data Quality Flags

 

Multiple validation flags were created:

 

- duplicate_order_id_flag 

- date_issue_flag 

- discount_issue_flag 

- calculation_mismatch_flag 

- status_summary_flag 

 

A final consolidated field:

 

**data_quality_flag**

- Clean 

- Warning 

- Invalid 

 

---

 

## 9. Business Rules Applied

 

- Missing region → replaced with "Unknown" 

- Missing ship mode → replaced with "Unknown" 

- Negative or invalid discounts → flagged 

- Cancelled and failed orders → excluded from completed sales 

- Refunded orders → analyzed separately 

- Ship date before order date → flagged as invalid 

 

---

 

## 10. Summary

 

The data cleaning process was designed to be:

 

- Transparent (using flags instead of deleting important records) 

- Reproducible (formula-based approach) 

- Reliable for analysis 

 

The cleaned dataset (`cleaned_orders.xlsx`) is now ready for further reporting and dashboard creation.

---



## 11. Limitations

The cleaning process is based only on the given dataset. 
Some assumptions were made while handling missing values, which may slightly affect the final analysis.


---


## 12. Reflection 
This cleaning approach allowed me to maintain transparency by not deleting all problematic records and instead flagging them for review. It ensures that business decisions are based on reliable and validated data.

While working on this dataset, I observed that even small data quality issues such as missing values, inconsistent formats, or duplicate entries can significantly impact analysis results.


Instead of simply deleting problematic data, I used a combination of cleaning and flagging approaches to maintain transparency and ensure that important business information was not lost.


This process helped me understand the importance of careful data preparation before performing analysis and how proper validation improves the reliability of business insight
