## Transpose Used Appropriately

### Objective
To convert rows into columns and columns into rows using the Transpose transformation, restructuring data layout to make it suitable for analysis and visualization in Power BI.

### Business Context
Transpose is a powerful transformation used when data is organized in a format that's convenient for data entry but not ideal for analysis. Common scenarios include:
- Monthly/quarterly data stored as column headers that need to be converted to rows for time-series analysis
- Survey responses where questions are columns but need to be rows
- Cross-tabulated reports that need to be normalized for proper data modeling

Proper use of Transpose enables better data modeling, easier filtering, and more flexible visualizations in Power BI.

### When to Use Transpose

**Appropriate Use Cases:**
- Converting pivot-style data to a normalized format
- Transforming wide tables (many columns) to tall tables (many rows)
- Restructuring time-period data from columns to rows
- Preparing data for unpivot operations

**When NOT to Use Transpose:**
- If Unpivot would be more appropriate (for maintaining column headers as values)
- When data is already in the correct structure
- If it would make the data less readable or harder to analyze

### Steps Performed

1. **Identified Data Requiring Transpose**
   - Analyzed the dataset structure
   - Found a table with Regional based sales data where Regions were stored as column headers
   - Determined that transpose would help convert this to a proper date-based format

2. **Created Reference Query**
   - Right-clicked on the source query
   - Selected **Reference** to preserve original data
   - Named the new query `Sales`
 
  *Screenshot showing how preserve original data*
  
   <img width="1920" height="1006" alt="image" src="https://github.com/user-attachments/assets/89486419-879c-4285-bec3-620d178bd498" />

3. **Applied Transpose Transformation**
   - Selected the table to transpose
   - Navigated to **Transform** tab in the ribbon
   - Clicked **Transpose** button
   - Power Query instantly swapped rows and columns

4. **Cleaned Up After Transpose**
   - Promoted first row to headers using **Use First Row as Headers**
   - Renamed columns appropriately
   - Changed data types as needed

5. **Verified Data Integrity**
   - Compared transposed data with original to ensure accuracy
   - Checked that all values were preserved correctly
   - Confirmed the new structure was suitable for analysis
  
