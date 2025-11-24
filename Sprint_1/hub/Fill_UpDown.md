## Fill Up/Down Applied Correctly

### Objective
To handle missing values in the dataset by filling blank cells with values from adjacent cells (above or below), ensuring data completeness and consistency for analysis.

### Business Context
When working with real-world datasets, it's common to encounter missing or blank values, especially in columns where data entry follows a merged cell pattern (e.g., customer names, categories, or date fields). The Fill Up/Down transformation ensures that every row has complete information, which is essential for accurate reporting and analysis in Power BI.

### Steps Performed

1. **Opened Power Query Editor**
   - Launched Power BI Desktop
   - Clicked on `Get Data` → Selected `Excel workbook`
   - Loaded sample dataset **orders.xlsx** into Power Query Editor

2. **Identified Missing Values**
   - Reviewed the dataset and identified blank cells in the `Customer Name` column
   - These blanks occurred because the source data had merged cells in Excel

*Screenshot showing the dataset with blank cells in CustomerName column*
<img width="1657" height="1029" alt="image" src="https://github.com/user-attachments/assets/fc8e8029-adec-4677-9c36-859d20185d4e" />

3. **Applied Fill Down Transformation**
   - Selected the `Customer Name` column
   - Navigated to **Transform** tab in the ribbon
   - Clicked **Fill** → Selected **Down**
   - Power Query automatically filled all blank cells with the value from the cell above

*Screenshot showing the Fill Down operation being applied from Transform tab*
<img width="1918" height="1031" alt="Transform in Power Query" src="https://github.com/user-attachments/assets/5b6aea78-48bd-4814-81e4-762be93bccd4" />

4. **Verified Results**
   - Checked that all previously blank cells now contained appropriate values
   - Ensured no data integrity issues were introduced

*Screenshot showing the result with all blank cells filled*
<img width="1918" height="1030" alt="Transform in Power Query 2" src="https://github.com/user-attachments/assets/77a5cf4d-050f-4734-9fc6-bc87d3470ec9" />

### Technical Details

**Transformation Applied:**
- **Column:** Customer Name
- **Operation:** Fill Down
- **Reason:** Source data had merged cells causing blanks in subsequent rows

*Before Transformation:*

<img width="491" height="134" alt="before transformation" src="https://github.com/user-attachments/assets/669b0573-dab0-44ba-abb2-e714c2f1929d" />

*After Transformation:*

<img width="489" height="135" alt="image" src="https://github.com/user-attachments/assets/7a2d5be2-0bb5-41a5-a7fa-f14e970e795f" />

### Results
- ✅ Successfully filled **2 blank cells** in the Customer Name column
- ✅ Maintained data integrity with no duplicate or incorrect values
- ✅ Dataset now ready for proper grouping and aggregation operations
- ✅ Improved data quality score from 85% to 100% completeness

### Key Learnings
- **Fill Down** is used when blank cells should inherit values from the cell above
- **Fill Up** is used when blank cells should inherit values from the cell below
- This transformation is essential for data exported from Excel with merged cells
- Always verify the logic before applying Fill operations to avoid propagating incorrect data

### Challenges Faced
**Challenge:** Initially, I wasn't sure whether to use Fill Down or Fill Up.

**Solution:** I analyzed the data pattern and determined that the blank cells represented continuation of the previous row's value (merged cell format), so Fill Down was the correct choice.

### Application in Project
This transformation is crucial for our Power BI reporting project because:
- Ensures all records have complete customer information
- Enables accurate customer-level analysis and grouping
- Prevents errors in calculated measures and aggregations
- Improves data visualization quality in final reports

---
