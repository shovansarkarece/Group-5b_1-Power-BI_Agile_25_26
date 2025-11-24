## Group By Table Created with Correct Aggregates

### Objective
To create summarized tables by grouping data based on specific columns and calculating meaningful aggregates (Sum, Average, Count, etc.) to support analytical reporting and business insights.

### Business Context
In business analytics, raw transactional data often needs to be summarized to answer key questions like "What is the total sales per product category?" or "How many orders did each customer place?" The Group By transformation in Power Query enables us to create these summary tables efficiently, which form the foundation for KPIs and dashboards in Power BI.

### Steps Performed

1. **Accessed Power Query Editor**
   - Opened the previously loaded dataset in Power Query Editor
   - Right-clicked on the query and selected **Reference** to create a new query for grouping (preserving original data)

*Screenshot showing the Reference option selection -*
<img width="1658" height="1028" alt="Reference option" src="https://github.com/user-attachments/assets/1f98468c-8097-4279-8ac4-449fec52eba2" />

2. **Configured Group By Transformation**
   - Selected the entire table
   - Navigated to **Transform** tab → Clicked **Group By**
   - Configured the Group By dialog box with the following settings

*Screenshot showing the Grouped By selection process -*
<img width="1917" height="1030" alt="Grouped By" src="https://github.com/user-attachments/assets/120bdd12-3ecf-4d52-869b-89e7b741f51b" />

3. **Created Multiple Aggregate Tables**
   
   **Grouping 1: Sales by Product Category**
   - Group by column: `Category`
   - New column name: `Sales_Profit`
   - Operation: `Sum`
   - Column: `Profit`
   
     *Screenshot showing the Grouped By selection process -*
     
     <img width="696" height="323" alt="image" src="https://github.com/user-attachments/assets/df4d2bb6-4e81-485a-8549-add3c68bfe0f" />

     *Screenshot showing how the group is formed -*
     
     <img width="353" height="92" alt="image" src="https://github.com/user-attachments/assets/4d98daab-b50d-455d-ac31-e8601389e465" />

   **Grouping 2: Customer Purchase Summary**
   - Group by column: `Region`
   - New column name: `Region_Based_Sales`
   - Operation: `Sum`
   - Column: `Sales`
  
     *Screenshot showing the Grouped By selection process -*
     
     <img width="696" height="323" alt="image" src="https://github.com/user-attachments/assets/2cfbb7bf-f494-45b7-bad1-9fca0bb26fb6" />

     *Screenshot showing how the Group is formed -*

     <img width="356" height="115" alt="image" src="https://github.com/user-attachments/assets/374d0975-7a29-415b-8d0e-741e13beb968" />

4. **Renamed Queries Appropriately**
   - Renamed grouped queries to `Sales_by_Region` and `Total_Sales`

     *Screenshot showing how queries renamed -

     <img width="801" height="304" alt="image" src="https://github.com/user-attachments/assets/b85f487f-b716-45ca-9906-ed8d6a3d099b" />

5. **Verified Aggregations**
   - Manually checked sample calculations to ensure accuracy
   - Compared totals with original dataset

### Available Aggregation Operations

Power Query supports the following aggregate functions:
- **Sum:** Total of all values
- **Average:** Mean of all values
- **Median:** Middle value
- **Min:** Smallest value
- **Max:** Largest value
- **Count Rows:** Number of rows in each group
- **Count Distinct Values:** Number of unique values

*Screenshot showing all queries in the Queries panel (raw data and grouped tables)*

<img width="715" height="400" alt="image" src="https://github.com/user-attachments/assets/71cc67d2-8a35-4946-aeb2-0badb637908d" />

### Results
- ✅ Created **2 summary tables** with meaningful aggregations
- ✅ Sales by Category table: **3 product categories** with total Profits
- ✅ Region based Summary table: **4 Regions** with the sales
- ✅ All calculations verified for accuracy
- ✅ Queries properly renamed and organized

### Key Learnings

1. **Reference vs Duplicate:**
   - Used **Reference** to create new queries based on original data
   - This ensures changes to source data automatically update all grouped tables
   - **Duplicate** creates an independent copy (not recommended for this use case)

2. **Multiple Aggregates:**
   - Can add multiple aggregate columns in a single Group By operation
   - Click **Add aggregation** button in the dialog to add more calculations

3. **Advanced Grouping:**
   - Can group by multiple columns (e.g., Category AND Region)
   - Simply click **Add grouping** in the Group By dialog

4. **Performance Considerations:**
   - Grouped tables are more efficient for visualizations
   - Reduces data volume while preserving analytical value

### Challenges Faced
   - **Challenge 1:** Initially, I created a duplicate query instead of a reference, which meant changes to the source wouldn't propagate.
   - **Solution:** Deleted the duplicate and created a reference query instead using right-click → Reference.
   - **Challenge 2:** Wasn't sure how to add multiple aggregates in one Group By operation.
   - **Solution:** Discovered the **Add aggregation** button in the Group By dialog, which allows adding multiple calculations simultaneously.
   - **Challenge 3:** Column names were auto-generated as "Count" instead of descriptive names.

**Solution:** Renamed columns to meaningful names for better clarity.

