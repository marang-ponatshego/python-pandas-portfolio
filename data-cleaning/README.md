# Data Cleaning in Pandas

## Overview

A pandas notebook demonstrating a full data cleaning workflow on a
raw customer call list. The raw file contains messy real-world issues:
inconsistent formatting, missing values, unusable columns, and text
that needs to be split into multiple fields.

**Tool:** Python — pandas
**File:** `data_cleaning.ipynb`
**Input data:** `customer_call_list.xlsx`

## What the notebook does

### 1. Load and inspect
- Reads the raw Excel file into a pandas DataFrame
- Inspects shape, column names, data types, and null counts
- Identifies which columns need cleaning and which need removal

### 2. Remove unhelpful columns
- Drops columns that carry no analytical value
  (e.g., "Not_Useful_Column")

### 3. Standardise text fields
- Strips inconsistent punctuation from phone numbers and names
- Fixes inconsistent formatting in the "Do_Not_Contact" flag
  (e.g., "Y", "N", "yes", "no" → single standard form)

### 4. Clean names and addresses
- Splits combined "Last_Name" strings where needed
- Trims whitespace and standardises capitalisation

### 5. Handle missing values
- Fills or removes NaN entries depending on the column's role
- Ensures essential fields (name, phone) are not null

### 6. Standardise phone numbers
- Removes non-numeric characters
- Applies consistent formatting so all numbers follow the same pattern

### 7. Filter and finalise
- Removes rows that should not be contacted
  (`Do_Not_Contact = Yes`) and rows with missing phone numbers
- Resets the index and exports the final clean dataset

## Key outputs

- A fully cleaned DataFrame ready for downstream use
- All personal-name, phone, and contact-flag fields standardised
- Clean separation between contactable and non-contactable customers

## Notes

- Raw data file (`customer_call_list.xlsx`) is included in this folder.
- The notebook uses a local file path — update the `pd.read_excel(...)`
  path to your own location before running.
- This is a portfolio demonstration of pandas cleaning operations —
  not a live business dataset.

## Skills demonstrated

- `pd.read_excel()` and DataFrame inspection (`info`, `describe`, `isna`)
- Column dropping and selection
- String operations: `.str.replace()`, `.str.strip()`, `.str.split()`
- Conditional filtering with `.loc[]`
- Null handling: `fillna`, `dropna`
- Index management: `reset_index`, `set_index`
- Exporting: `to_excel()` / `to_csv()`
