## Columns and Rows Cleaned (Kept/Removed)

### Objective
To improve data quality and optimize performance by removing unnecessary columns and rows, keeping only relevant data required for analysis and reporting in Power BI.

### Business Context
Raw datasets often contain:
- Unnecessary columns (metadata, internal IDs, redundant information)
- Invalid rows (headers, footers, blank rows, error rows)
- Duplicate records
- Test data or sample records

Cleaning data by removing irrelevant columns and rows:
- **Improves performance:** Smaller datasets load and refresh faster
- **Enhances clarity:** Focuses analysis on relevant information
- **Reduces errors:** Eliminates problematic or inconsistent data
- **Optimizes storage:** Reduces file size and memory usage
- **Simplifies modeling:** Makes relationships and calculations clearer

### Data Cleaning Strategy

**Columns to Remove:**
- Internal system IDs not needed for reporting
- Redundant or duplicate information
- Empty columns with no data
- Columns with sensitive information (if not needed)
- Metadata columns (created_by, modified_by, etc.)

**Rows to Remove:**
- Header rows repeated in the middle of data
- Footer rows with totals or notes
- Blank/empty rows
- Duplicate rows
- Error rows with invalid data
- Test records

### Steps Performed

#### Part A: Removing Unnecessary Columns

1. **Identified Columns for Removal**
   - Reviewed all columns in the dataset
   - Identified columns not required for analysis:
     - `Ship Mode` (system-generated, not needed for reports)
     - `Segment` (data, not relevant)
     - `Notes` (empty column with no data)
     - `Column1` (unnamed column with null values)

2. **Removed Individual Columns**
   - Right-clicked on `Ship Mode` column header
   - Selected **Remove**
   - Repeated for other unnecessary columns

3. **Used "Remove Other Columns" for Efficiency**
   - Selected all columns to KEEP (Ctrl+Click)
   - Right-clicked on selection
   - Selected **Remove Other Columns**
   - This kept only relevant columns in one operation

4. **Verified Column Removal**
   - Checked that only business-relevant columns remained
   - Ensured no critical data was accidentally removed

#### Part B: Removing Unnecessary Rows

1. **Removed Top Rows (Header Rows)**
   - Identified that first 2 rows contained report title and metadata
   - Went to **Home** tab → **Remove Rows** → **Remove Top Rows**
   - Entered `2` to remove first 2 rows

2. **Removed Bottom Rows (Footer Rows)**
   - Identified last 3 rows contained summary totals and notes
   - Went to **Home** tab → **Remove Rows** → **Remove Bottom Rows**
   - Entered `3` to remove last 3 rows

3. **Removed Blank Rows**
   - Went to **Home** tab → **Remove Rows** → **Remove Blank Rows**
   - Automatically removed all rows where all columns were empty
   - Cleaned up 5 blank rows in the dataset

4. **Removed Duplicate Rows**
   - Went to **Home** tab → **Remove Rows** → **Remove Duplicates**
   - Power Query identified and removed duplicate records
   - Found and removed 8 duplicate entries

5. **Removed Rows with Errors**
   - Identified rows with error values in certain columns
   - Went to **Home** tab → **Remove Rows** → **Remove Errors**
   - Removed 2 rows containing error values

6. **Removed Rows Based on Condition (Custom Filter)**
   - Needed to remove test records where `Customer Name` = "Test Customer"
   - Clicked dropdown on `Customer Name` column
   - Unchecked "Test Customer"
   - Applied filter to exclude test records

### Technical Details

#### Column Removal Summary

**Original Columns (24 total):**

1. Row ID ✅ KEPT
2. Order ID ✅ KEPT
4. Order Date ✅ KEPT
5. Ship date ✅ KEPT
6. Ship Mode ❌ REMOVED (not needed)
7. Customer ID  ✅ KEPT
8. Customer Name ✅ KEPT
9. Segment  ❌ REMOVED (not needed)
10. Country
11. City
12. State
13. Postal Code ❌ REMOVED (not needed)
14. Region
15. Product ID ❌ REMOVED (not needed)
17. Category ✅ KEPT
18. Sub-Category ❌ REMOVED (not needed)
20. Product Name ✅ KEPT
21. Sales ✅ KEPT
22. Quantity ✅ KEPT
23. Discount ❌ REMOVED (not needed)
24. Profit ✅ KEPT

**Cleaned Dataset (8 columns):**

1. Ship Mode
2. Segment
3. Postal Code
4. Product ID
5. Sub-Category
6. Discount

**Columns Removed:** 6  
**Columns Retained:** 18  
**Reduction:** 25% fewer columns




