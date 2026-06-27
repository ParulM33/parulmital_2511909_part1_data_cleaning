# Data Cleaning Log

## Issues Identified

When I started exploring the dataset, I noticed several data quality issues. 
There were missing values in fields like region and discount, inconsistent text formats, duplicate records, and some incorrect date entries. 
I also identified cases where ship date was earlier than order date, which is not valid.

## Cleaning Actions Performed

I first cleaned all text fields by removing extra spaces and standardizing formats using Excel functions like TRIM and PROPER. 
Then I handled missing values by either filling them with "Unknown" or keeping them flagged based on business rules. 
Duplicate rows were identified and removed, while conflicting duplicates were flagged instead of being deleted.

## Business Rules Applied

Missing region and ship mode were replaced with "Unknown". 
Missing discount was treated as 0 only when other sales values were valid. 
Negative or unusually high discounts were flagged as invalid. 
Cancelled, refunded, or failed orders were excluded from final sales calculations.

## Assumptions

I assumed missing region values represent unknown entries. 
I also assumed discount values should not be modified unless clearly invalid.

## Records Removed / Flagged

Exact duplicate records were removed. 
Duplicate order IDs with mismatched data were flagged for further review instead of deletion.

## Limitations

The cleaning process is based only on the given dataset. 
Some assumptions were made while handling missing values, which may slightly affect the final analysis.
