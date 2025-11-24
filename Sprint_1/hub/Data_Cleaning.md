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


