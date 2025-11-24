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





## From here write further
##
##




3. **Created Multiple Aggregate Tables**
   
   **Grouping 1: Sales by Product Category**
   - Group by column: `Category`
   - New column name: `Total_Sales`
   - Operation: `Sum`
   - Column: `Sales_Amount`
   - Additional aggregate: `Order_Count` (Operation: Count Rows)

   **Grouping 2: Customer Purchase Summary**
   - Group by column: `CustomerName`
   - New column name: `Total_Purchases`
   - Operation: `Sum`
   - Column: `Sales_Amount`
   - Additional aggregate: `Number_of_Orders` (Operation: Count Rows)
   - Additional aggregate: `Average_Order_Value` (Operation: Average, Column: Sales_Amount)

4. **Renamed Queries Appropriately**
   - Renamed grouped queries to `Sales_by_Category` and `Customer_Summary`
   - Kept original query as `Sales_Data_Raw`

5. **Verified Aggregations**
   - Manually checked sample calculations to ensure accuracy
   - Compared totals with original dataset

### Technical Details

**Aggregation 1: Sales by Product Category**

**Configuration:**
```
Group By Column: Category
Aggregations:
  - Total_Sales (Sum of Sales_Amount)
  - Order_Count (Count Rows)
```

**Before Grouping (Raw Data Sample):**
```
| OrderID | Category    | Product      | Sales_Amount |
|---------|-------------|--------------|--------------|
| 101     | Electronics | Laptop       | 1200         |
| 102     | Electronics | Mouse        | 25           |
| 103     | Electronics | Keyboard     | 75           |
| 104     | Furniture   | Desk         | 350          |
| 105     | Furniture   | Chair        | 150          |
```

**After Grouping:**
```
| Category    | Total_Sales | Order_Count |
|-------------|-------------|-------------|
| Electronics | 1300        | 3           |
| Furniture   | 500         | 2           |
```

---

**Aggregation 2: Customer Purchase Summary**

**Configuration:**
```
Group By Column: CustomerName
Aggregations:
  - Total_Purchases (Sum of Sales_Amount)
  - Number_of_Orders (Count Rows)
  - Average_Order_Value (Average of Sales_Amount)
```

**Before Grouping (Raw Data Sample):**
```
| OrderID | CustomerName | Sales_Amount |
|---------|--------------|--------------|
| 101     | John Smith   | 1200         |
| 102     | John Smith   | 25           |
| 103     | John Smith   | 75           |
| 104     | Sarah Jones  | 350          |
| 105     | Sarah Jones  | 150          |
```

**After Grouping:**
```
| CustomerName | Total_Purchases | Number_of_Orders | Average_Order_Value |
|--------------|-----------------|------------------|---------------------|
| John Smith   | 1300            | 3                | 433.33              |
| Sarah Jones  | 500             | 2                | 250.00              |
```

### Available Aggregation Operations

Power Query supports the following aggregate functions:
- **Sum:** Total of all values
- **Average:** Mean of all values
- **Median:** Middle value
- **Min:** Smallest value
- **Max:** Largest value
- **Count Rows:** Number of rows in each group
- **Count Distinct Values:** Number of unique values
- **Standard Deviation:** Measure of data spread

### Screenshots

![Group By Dialog - Configuration](assets/screenshots/task2_groupby_dialog.png)
*Screenshot showing the Group By dialog box with column selection and aggregate configuration*

![Sales by Category - Result](assets/screenshots/task2_sales_by_category.png)
*Screenshot showing the grouped table: Sales by Product Category with aggregates*

![Customer Summary - Result](assets/screenshots/task2_customer_summary.png)
*Screenshot showing the grouped table: Customer Purchase Summary with multiple aggregates*

![Power Query Queries Panel](assets/screenshots/task2_queries_panel.png)
*Screenshot showing all queries in the Queries panel (raw data and grouped tables)*

### Results
- ✅ Created **2 summary tables** with meaningful aggregations
- ✅ Sales by Category table: **3 product categories** with total sales and order counts
- ✅ Customer Summary table: **12 unique customers** with purchase totals, order counts, and averages
- ✅ All calculations verified for accuracy
- ✅ Queries properly named and organized

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

**Challenge 1:** Initially, I created a duplicate query instead of a reference, which meant changes to the source wouldn't propagate.

**Solution:** Deleted the duplicate and created a reference query instead using right-click → Reference.

**Challenge 2:** Wasn't sure how to add multiple aggregates in one Group By operation.

**Solution:** Discovered the **Add aggregation** button in the Group By dialog, which allows adding multiple calculations simultaneously.

**Challenge 3:** Column names were auto-generated as "Count" instead of descriptive names.

**Solution:** Renamed columns to meaningful names like `Order_Count` and `Average_Order_Value` for better clarity.

### Application in Project

These grouped tables will be used for:
- **Category Performance Dashboard:** Showing total sales and order volume by product category
- **Customer Segmentation:** Identifying high-value customers based on total purchases
- **Sales Analysis:** Understanding average order values and purchase patterns
- **KPI Calculations:** Creating measures for top customers, best-selling categories, etc.

### Best Practices Applied

1. ✅ Created reference queries to maintain data lineage
2. ✅ Used descriptive names for aggregate columns
3. ✅ Verified calculations against source data
4. ✅ Documented the business purpose of each aggregation
5. ✅ Organized queries logically in the Queries panel
6. ✅ Kept raw data intact for detailed analysis when needed

### SQL Equivalent (For Reference)

The Power Query Group By operation is equivalent to this SQL query:
```sql
-- Sales by Category
SELECT 
    Category,
    SUM(Sales_Amount) AS Total_Sales,
    COUNT(*) AS Order_Count
FROM Sales_Data
GROUP BY Category;

-- Customer Summary
SELECT 
    CustomerName,
    SUM(Sales_Amount) AS Total_Purchases,
    COUNT(*) AS Number_of_Orders,
    AVG(Sales_Amount) AS Average_Order_Value
FROM Sales_Data
GROUP BY CustomerName;
```

---

