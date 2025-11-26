# Power BI Data Transformation Tasks - Complete Guide

## Table of Contents
1. [Numeric Fields Updated Using Number Transform](#task-1-numeric-fields-updated-using-number-transform)
2. [Date Columns Enriched Using Add Column → Date Functions](#task-2-date-columns-enriched-using-add-column--date-functions)
3. [Multiple Sheets Successfully Appended Into One](#task-3-multiple-sheets-successfully-appended-into-one)
4. [Different Tables Correctly Merged Using Join Keys](#task-4-different-tables-correctly-merged-using-join-keys)
5. [Conditional Column Created Using Add Column → Conditional Column](#task-5-conditional-column-created-using-add-column--conditional-column)

---

## Prerequisites

Before starting, ensure you have:
- **Power BI Desktop** installed (free version)
- **Sample data** (Excel file, CSV, or any data source)
- At least **2 sheets or tables** for appending/merging tasks
- A **date column** for date transformation tasks
- **Numeric columns** for number transformations

---

## Task 1: Numeric Fields Updated Using Number Transform

### Objective
Transform numeric columns by applying mathematical operations such as rounding, multiplication, division, or changing decimal places.

### Step-by-Step Instructions

#### Step 1: Open Power BI Desktop
- Launch **Power BI Desktop** application

#### Step 2: Load Your Data
1. Click **"Home"** tab
2. Click **"Get Data"** button
3. Choose your data source:
   - Excel Workbook
   - CSV
   - SQL Database
   - Web
   - Or any other source
4. Navigate to your file and click **"Open"**

#### Step 3: Open Power Query Editor
1. In the Navigator window, select your table/sheet
2. Click **"Transform Data"** button (not "Load")
3. This opens the **Power Query Editor** window

#### Step 4: Select Numeric Column
- Click on the **header** of any numeric column (e.g., Sales, Price, Quantity, Revenue)

#### Step 5: Apply Number Transformation
1. Go to the **"Transform"** tab in the ribbon
2. Click the **"Number"** dropdown menu
3. Choose from available transformations:

**Common Transformations:**
- **Round** → Round to specified decimal places
- **Round Up** → Always round up
- **Round Down** → Always round down
- **Absolute Value** → Remove negative signs (make all positive)
- **Multiply** → Multiply by a number (e.g., 100 for percentages)
- **Divide** → Divide by a number (e.g., 1000 for thousands)
- **Percentage** → Convert to percentage format
- **Standard** → Format as standard number (set decimal places)
- **Scientific** → Convert to scientific notation

#### Step 6: Configure the Transformation
For example, to round to 2 decimal places:
1. Select **"Round"**
2. Enter **"2"** for decimal places
3. Click **OK**

#### Example Scenarios

**Scenario 1: Round Sales to 2 Decimals**
- Original: 1234.567890
- Select "Sales" column → Transform → Number → Round → 2 decimals
- Result: 1234.57

**Scenario 2: Convert to Thousands**
- Original: 50000
- Select "Revenue" column → Transform → Number → Divide → Enter 1000
- Result: 50 (now in thousands)

**Scenario 3: Calculate Percentage**
- Original: 0.8567
- Select "Growth Rate" column → Transform → Number → Multiply → Enter 100
- Result: 85.67

#### Step 7: Verify the Transformation
- Check the **Applied Steps** panel on the right
- You'll see a new step like "Rounded Numbers" or "Multiplied Column"
- Preview the results in the data grid

---

## Task 2: Date Columns Enriched Using Add Column → Date Functions

### Objective
Extract additional date-related information (Year, Month, Quarter, Day, etc.) from existing date columns to enable time-based analysis.

### Step-by-Step Instructions

#### Step 1: Locate Your Date Column
In Power Query Editor, identify your date column (e.g., Order Date, Transaction Date, Invoice Date)

#### Step 2: Select the Date Column
- Click on the **header** of your date column

#### Step 3: Access Date Functions
1. Go to the **"Add Column"** tab in the ribbon
2. Click the **"Date"** dropdown button
3. You'll see various date extraction options

#### Step 4: Choose Date Functions to Extract

**Available Date Functions:**

| Function | Output | Example (from 2024-11-26) |
|----------|--------|---------------------------|
| **Year** | Year number | 2024 |
| **Month** | Month number (1-12) | 11 |
| **Month Name** | Full month name | November |
| **Quarter** | Quarter number (1-4) | 4 |
| **Day** | Day of month (1-31) | 26 |
| **Day of Week** | Day number (0-6) | 2 |
| **Day Name** | Weekday name | Tuesday |
| **Week of Year** | Week number (1-52) | 48 |
| **Start of Year** | First day of year | 2024-01-01 |
| **Start of Month** | First day of month | 2024-11-01 |
| **Start of Quarter** | First day of quarter | 2024-10-01 |
| **End of Month** | Last day of month | 2024-11-30 |
| **Age** | Years since date | Calculated age |

#### Step 5: Extract Multiple Date Components

**Example: Extract Year, Month, and Quarter**

1. Select date column → Add Column → Date → **Year**
   - New column created: "Year"

2. Select date column again → Add Column → Date → **Month**
   - New column created: "Month"

3. Select date column again → Add Column → Date → **Month Name**
   - New column created: "Month Name"

4. Select date column again → Add Column → Date → **Quarter**
   - New column created: "Quarter"

5. Select date column again → Add Column → Date → **Day Name**
   - New column created: "Day Name"

#### Step 6: Rename Columns (Optional but Recommended)
1. Double-click on the new column header
2. Give it a descriptive name:
   - "Year" → "Order Year"
   - "Month" → "Order Month"
   - "Quarter" → "Order Quarter"

#### Example Scenario

**Original Data:**
```
Order Date: 2024-11-26
```

**After Applying Date Functions:**
```
Order Date: 2024-11-26
Order Year: 2024
Order Month: 11
Order Month Name: November
Order Quarter: 4
Order Day: 26
Order Day Name: Tuesday
Order Week: 48
```

#### Step 7: Verify Results
- Check that new columns appear with correct values
- Review the **Applied Steps** panel for each extraction step

---

## Task 3: Multiple Sheets Successfully Appended Into One

### Objective
Combine multiple Excel sheets or tables with the **same column structure** into a single unified table (vertical stacking).

### When to Use Append
- Multiple sheets with identical columns (e.g., Sales_Jan, Sales_Feb, Sales_Mar)
- Monthly/quarterly data files with same structure
- Data split across multiple files that need consolidation

### Step-by-Step Instructions

#### Method 1: Append Queries (Recommended for 2-3 Tables)

**Step 1: Load All Sheets**
1. Click **"Get Data"** → Excel
2. In Navigator window, **check multiple sheets** you want to combine
3. Click **"Transform Data"** (loads all sheets to Power Query)

**Step 2: Open Append Queries Dialog**
1. In Power Query Editor, go to **"Home"** tab
2. Click **"Append Queries"** dropdown
3. Choose:
   - **"Append Queries"** → For 2 tables only
   - **"Append Queries as New"** → Creates new combined table (recommended)

**Step 3: Select Tables to Append**
1. If 2 tables: Select the second table
2. If 3+ tables: Choose **"Three or more tables"**
3. Move tables from "Available tables" to "Tables to append"
4. Order matters if you care about sequence
5. Click **OK**

**Step 4: Verify the Result**
- New query created with combined data
- Row count = sum of all individual tables
- Check that all columns are present

#### Method 2: Combine Files (Best for Many Sheets)

**Step 1: Prepare Your Files**
- Ensure all sheets/files have **identical column names**
- Same column order (preferred but not required)
- Same data types in each column

**Step 2: Combine Files**
1. Get Data → Excel → Select file
2. In Navigator, you'll see all sheets
3. Click **"Transform Data"** on one sheet
4. Go to **"Home"** → **"Append Queries"** → **"Append Queries as New"**
5. Select **"Three or more tables"**
6. Select all sheets
7. Click **OK**

#### Example Scenario

**Before Appending:**
```
Sheet: Sales_January (100 rows)
Columns: Order ID | Date | Product | Amount | Region

Sheet: Sales_February (150 rows)
Columns: Order ID | Date | Product | Amount | Region

Sheet: Sales_March (120 rows)
Columns: Order ID | Date | Product | Amount | Region
```

**After Appending:**
```
Combined Sales (370 rows)
Columns: Order ID | Date | Product | Amount | Region
- All data from January, February, and March combined
```

#### Step 5: Add Source Column (Optional)
To track which sheet data came from:
1. Before appending, add a custom column to each table
2. Add Column → Custom Column
3. Name: "Source Month"
4. Formula: `"January"` (or respective month)
5. Then append all tables

#### Common Issues and Solutions

**Issue 1: Column Names Don't Match**
- Solution: Rename columns before appending
- Right-click column header → Rename

**Issue 2: Extra Columns in Some Tables**
- Solution: Remove extra columns before appending
- Or Power BI will add them with null values

**Issue 3: Different Data Types**
- Solution: Ensure same data type in all tables
- Transform → Data Type → Choose correct type

---

## Task 4: Different Tables Correctly Merged Using Join Keys

### Objective
Combine two tables with **different columns** using a common column (join key), similar to VLOOKUP in Excel or SQL JOIN operations.

### When to Use Merge
- Enriching main table with additional information
- Looking up values from a reference table
- Combining Orders with Customer details
- Adding Product information to Sales data

### Step-by-Step Instructions

#### Step 1: Load Both Tables
1. Get Data → Load your **primary table** (e.g., Orders)
2. Get Data → Load your **secondary table** (e.g., Customers)
3. Both tables now appear in Power Query

#### Step 2: Select Primary Table
- Click on your **main table** (the one you want to keep all records from)
- This is typically your transactional or fact table

#### Step 3: Start Merge Operation
1. Go to **"Home"** tab
2. Click **"Merge Queries"** dropdown
3. Choose:
   - **"Merge Queries"** → Merges into current table
   - **"Merge Queries as New"** → Creates new merged table (recommended)

#### Step 4: Configure the Merge

**In the Merge Dialog:**

1. **Select the second table** from the dropdown
2. **Select the matching column** in the first table (click column header)
3. **Select the matching column** in the second table (click column header)
   - Common join keys: Customer ID, Product ID, Order ID, Date
4. **Choose Join Kind:**

**Join Types Explained:**

| Join Type | Description | When to Use |
|-----------|-------------|-------------|
| **Left Outer** | Keep all rows from first table, add matching from second | Most common - keep all orders, add customer details |
| **Right Outer** | Keep all rows from second table, add matching from first | Opposite of Left Outer |
| **Full Outer** | Keep all rows from both tables | When you need everything |
| **Inner** | Only keep rows that match in both tables | When you only want complete records |
| **Left Anti** | Keep rows from first table with NO match in second | Find orders without customer |
| **Right Anti** | Keep rows from second table with NO match in first | Find customers without orders |

5. Click **OK**

#### Step 5: Expand the Merged Column

After merging, you'll see a new column with **"Table"** values:

1. Click the **expand icon** (↕️ two arrows) in the merged column header
2. A list of columns from the second table appears
3. **Check the columns** you want to include
4. **Uncheck** "Use original column name as prefix" (optional - removes table name prefix)
5. Click **OK**

#### Step 6: Verify the Merge
- Check that new columns appear with correct data
- Verify row count (depends on join type)
- Look for null values where data didn't match

#### Example Scenarios

**Scenario 1: Add Customer Names to Orders**

**Table 1: Orders**
```
Order ID | Customer ID | Product    | Amount
1001     | C101        | Laptop     | 1200
1002     | C102        | Mouse      | 25
1003     | C101        | Keyboard   | 75
```

**Table 2: Customers**
```
Customer ID | Customer Name | City
C101        | John Smith    | New York
C102        | Jane Doe      | London
C103        | Bob Wilson    | Paris
```

**After Merge (Left Outer on Customer ID):**
```
Order ID | Customer ID | Product  | Amount | Customer Name | City
1001     | C101        | Laptop   | 1200   | John Smith    | New York
1002     | C102        | Mouse    | 25     | Jane Doe      | London
1003     | C101        | Keyboard | 75     | John Smith    | New York
```

**Scenario 2: Add Product Details to Sales**

**Table 1: Sales**
```
Sale ID | Product ID | Quantity
S001    | P10        | 5
S002    | P20        | 3
```

**Table 2: Products**
```
Product ID | Product Name | Category     | Unit Price
P10        | Laptop       | Electronics  | 1200
P20        | Mouse        | Accessories  | 25
P30        | Monitor      | Electronics  | 300
```

**After Merge (Left Outer on Product ID):**
```
Sale ID | Product ID | Quantity | Product Name | Category    | Unit Price
S001    | P10        | 5        | Laptop       | Electronics | 1200
S002    | P20        | 3        | Mouse        | Accessories | 25
```

#### Common Issues and Solutions

**Issue 1: No Common Column**
- Solution: You need at least one matching column to merge
- Create a common key column if needed

**Issue 2: Different Column Names for Join Key**
- Solution: Rename one column to match the other
- Or select different columns in merge dialog

**Issue 3: Too Many Rows After Merge**
- Solution: You might have duplicate keys causing cartesian joins
- Check for duplicate IDs in your lookup table

**Issue 4: Null Values After Merge**
- Solution: This means no match was found
- Check data quality in both tables
- Verify exact match (watch for extra spaces)

---

## Task 5: Conditional Column Created Using Add Column → Conditional Column

### Objective
Create a new column based on IF-THEN-ELSE logic, similar to Excel's IF function, to categorize or flag data based on conditions.

### When to Use Conditional Columns
- Categorize sales as High/Medium/Low
- Flag orders as Urgent/Normal based on amount
- Classify customers by age groups
- Create status indicators
- Apply business rules to data

### Step-by-Step Instructions

#### Step 1: Access Conditional Column
1. In **Power Query Editor**
2. Go to **"Add Column"** tab
3. Click **"Conditional Column"** button

#### Step 2: Configure Conditional Logic

**In the Conditional Column Dialog:**

1. **New column name:** Enter a descriptive name (e.g., "Sales Category", "Age Group", "Priority")

2. **Set up conditions:**
   - **Column Name:** Select the column to evaluate
   - **Operator:** Choose comparison operator
   - **Value:** Enter or select the value to compare
   - **Output:** Enter the result if condition is TRUE

3. **Add more conditions:**
   - Click **"Add Clause"** for additional IF conditions
   - Conditions are evaluated top to bottom

4. **Else clause:**
   - Enter the default output if no conditions match

5. Click **OK**

#### Operators Available

| Operator | Description | Example |
|----------|-------------|---------|
| **equals** | Exact match | Status equals "Active" |
| **does not equal** | Not equal | Region does not equal "North" |
| **greater than** | Numeric comparison | Sales > 10000 |
| **greater than or equal to** | Inclusive comparison | Age >= 18 |
| **less than** | Numeric comparison | Quantity < 5 |
| **less than or equal to** | Inclusive comparison | Score <= 50 |
| **begins with** | Text starts with | Name begins with "A" |
| **does not begin with** | Text doesn't start with | Code does not begin with "X" |
| **ends with** | Text ends with | Email ends with ".com" |
| **does not end with** | Text doesn't end with | File does not end with ".pdf" |
| **contains** | Text includes substring | Description contains "urgent" |
| **does not contain** | Text doesn't include | Address does not contain "PO Box" |

#### Example Scenarios

**Example 1: Sales Performance Categories**

**Objective:** Categorize sales as High, Medium, or Low

**Setup:**
- New column name: **Sales Category**
- If **Sales** greater than **10000** then **High**
- Add Clause: If **Sales** greater than or equal to **5000** then **Medium**
- Else: **Low**

**Result:**
```
Sales Amount | Sales Category
15000        | High
8000         | Medium
3000         | Low
12000        | High
4500         | Low
```

**Example 2: Age Group Classification**

**Objective:** Group customers by age ranges

**Setup:**
- New column name: **Age Group**
- If **Age** less than **18** then **Minor**
- Add Clause: If **Age** less than **30** then **Young Adult**
- Add Clause: If **Age** less than **50** then **Adult**
- Add Clause: If **Age** less than **65** then **Middle Age**
- Else: **Senior**

**Result:**
```
Age | Age Group
15  | Minor
25  | Young Adult
40  | Adult
55  | Middle Age
70  | Senior
```

**Example 3: Order Priority Based on Amount**

**Objective:** Flag high-value orders for priority processing

**Setup:**
- New column name: **Priority**
- If **Order Amount** greater than or equal to **5000** then **Urgent**
- Add Clause: If **Order Amount** greater than or equal to **1000** then **High**
- Else: **Normal**

**Result:**
```
Order Amount | Priority
6500         | Urgent
2500         | High
500          | Normal
5000         | Urgent
```

**Example 4: Customer Status Based on Text**

**Objective:** Categorize customers based on membership type

**Setup:**
- New column name: **Membership Level**
- If **Membership** equals **"Gold"** then **Premium**
- Add Clause: If **Membership** equals **"Silver"** then **Standard**
- Else: **Basic**

**Result:**
```
Membership | Membership Level
Gold       | Premium
Silver     | Standard
Bronze     | Basic
Gold       | Premium
```

**Example 5: Geographic Region Classification**

**Objective:** Group states into regions

**Setup:**
- New column name: **Region**
- If **State** equals **"CA"** then **West**
- Add Clause: If **State** equals **"NY"** then **East**
- Add Clause: If **State** equals **"TX"** then **South**
- Else: **Other**

#### Step 3: Alternative - Using Custom Column for Complex Logic

For more complex conditions, use **Custom Column** with M code:

1. Add Column → **Custom Column**
2. Name your column
3. Use formula:

```m
= if [Sales] > 10000 then "High"
  else if [Sales] > 5000 then "Medium"
  else "Low"
```

**Advanced Example with Multiple Conditions:**
```m
= if [Sales] > 10000 and [Region] = "North" then "High Priority"
  else if [Sales] > 5000 or [Customer Type] = "VIP" then "Medium Priority"
  else "Low Priority"
```

#### Common Issues and Solutions

**Issue 1: Wrong Results**
- Solution: Check order of conditions (top to bottom evaluation)
- Most restrictive conditions should be first

**Issue 2: Null Values in Output**
- Solution: Add condition to handle null inputs
- Or use "Else" clause to catch all remaining cases

**Issue 3: Text Not Matching**
- Solution: Check for extra spaces
- Use "Trim" transformation before creating conditional column

**Issue 4: Need Complex Logic**
- Solution: Use Custom Column with M code instead
- Allows AND, OR, nested conditions

---

## General Tips and Best Practices

### Working in Power Query Editor

✅ **Do's:**
- Always transform data in Power Query, not in Report View
- Use descriptive names for new columns
- Keep track of Applied Steps (right panel)
- Test transformations with a subset of data first
- Document complex transformations with comments

❌ **Don'ts:**
- Don't modify data directly in Report View
- Don't skip "Close & Apply" - changes won't save
- Don't delete Applied Steps without understanding impact
- Don't mix data types in same column

### Saving Your Work

1. After completing all transformations in Power Query
2. Click **"Close & Apply"** in top-left corner
3. Wait for data to load into Power BI
4. **Save your .pbix file:** File → Save As
5. Give it a descriptive name

### Viewing Your Transformations

**Applied Steps Panel (Right Side):**
- Shows each transformation in order
- Click any step to see data at that point
- Delete steps by clicking X
- Rename steps for clarity

### Troubleshooting Common Issues

**Issue: Column Not Found Error**
- Cause: Column name changed or deleted in previous step
- Solution: Check earlier steps, ensure column exists

**Issue: Data Type Errors**
- Cause: Wrong data type for operation
- Solution: Transform → Data Type → Choose correct type

**Issue: Duplicate Columns**
- Cause: Multiple transformations creating same column
- Solution: Remove or rename duplicate columns

**Issue: Performance is Slow**
- Cause: Too many transformations or large dataset
- Solution: Filter early, remove unnecessary columns, use Query Folding

---

## Complete Workflow Example

Let's combine all 5 tasks in a real scenario:

### Scenario: Sales Analysis Dashboard

**Starting Data:**
- **3 Excel sheets:** Sales_Q1, Sales_Q2, Sales_Q3
- **Customers table:** Customer ID, Name, City, Region
- **Products table:** Product ID, Name, Category, Price

**Goal:** Create a unified sales dataset with all transformations

### Step-by-Step Workflow

**1. Load All Data**
- Get Data → Excel → Load all 3 sales sheets
- Get Data → Excel → Load Customers table
- Get Data → Excel → Load Products table

**2. Transform Numbers (Task 1)**
- Select Sales Amount column
- Transform → Number → Round → 2 decimals

**3. Enrich Dates (Task 2)**
- Select Order Date column
- Add Column → Date → Year
- Add Column → Date → Month Name
- Add Column → Date → Quarter

**4. Append Sales Sheets (Task 3)**
- Home → Append Queries as New
- Select Sales_Q1, Sales_Q2, Sales_Q3
- Name: "All Sales"

**5. Merge with Customers (Task 4)**
- Select "All Sales" table
- Home → Merge Queries
- Join on Customer ID (Left Outer)
- Expand: Customer Name, City, Region

**6. Merge with Products (Task 4 again)**
- Stay in "All Sales" table
- Home → Merge Queries
- Join on Product ID (Left Outer)
- Expand: Product Name, Category, Unit Price

**7. Create Sales Category (Task 5)**
- Add Column → Conditional Column
- Name: Sales Category
- If Sales Amount > 5000 then "High"
- Else if Sales Amount > 1000 then "Medium"
- Else: "Low"

**8. Finalize**
- Review all columns
- Remove unnecessary columns
- Rename columns for clarity
- Close & Apply

**Final Result:**
A comprehensive sales dataset ready for visualization with:
- All quarterly sales combined
- Rounded sales amounts
- Date components extracted
- Customer information added
- Product details included
- Sales categorization applied

---

## Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Open Power Query | Transform Data button |
| Rename Column | Double-click header |
| Delete Column | Select → Right-click → Remove |
| Change Data Type | Select → Transform → Data Type |
| Add Custom Column | Add Column → Custom Column |
| Undo Step | Delete from Applied Steps |
| Close & Apply | Alt + F4 → Yes |

---

## Additional Resources

### Official Microsoft Documentation
- [Power Query M Formula Language](https://learn.microsoft.com/en-us/powerquery-m/)
- [Power BI Data Transformation](https://learn.microsoft.com/en-us/power-bi/transform-model/)
- [Merge Queries](https://learn.microsoft.com/en-us/power-query/merge-queries-overview)
- [Append Queries](https://learn.microsoft.com/en-us/power-query/append-queries)

### Learning Resources
- Microsoft Learn: Power BI Learning Path
- Power BI Community Forums
- YouTube: "Guy in a Cube" channel
- SQLBI.com for DAX and modeling

---

## Summary Checklist

After completing this guide, you should be able to:

- ✅ Transform numeric columns using Number operations
- ✅ Extract date components (Year, Month, Quarter, etc.)
- ✅ Append multiple sheets/tables into one
- ✅ Merge different tables using join keys
- ✅ Create conditional columns with business logic
- ✅ Navigate Power Query Editor confidently
- ✅ Understand Applied Steps and transformation flow
- ✅ Save and apply transformations to your data model

---

## Next Steps

1. **Practice each task** with sample data
2. **Combine tasks** in real projects
3. **Learn DAX** for calculated measures in Report View
4. **Create visualizations** with your transformed data
5. **Build dashboards** and share insights

---

## Conclusion

These five core Power BI data transformation tasks form the foundation of data preparation for analytics. Mastering Power Query Editor and these transformations will enable you to:

- Clean and prepare data efficiently
- Combine data from multiple sources
- Enrich datasets with calculated fields
- Apply business logic consistently
- Create analysis-ready data models

Remember: **Good data preparation = Great insights!**

Power BI's strength lies in its ability to connect, transform, and visualize data seamlessly. With these skills, you're well-equipped to build professional business intelligence solutions.

---

**Document Version:** 1.0  
**Last Updated:** November 2025  
**Author:** Power BI Training Guide  
**For:** Data Analysts, Business Intelligence Professionals, Power BI Learners

---

## Appendix: Quick Reference Tables

### Number Transform Options
| Operation | Use Case |
|-----------|----------|
| Round | Clean decimal values |
| Absolute Value | Remove negatives |
| Multiply | Convert units (e.g., × 100 for %) |
| Divide | Scale down large numbers |
| Percentage | Format as percentage |

### Date Functions Quick Reference
| Function | Output Example |
|----------|----------------|
| Year | 2024 |
| Month | 11 |
| Month Name | November |
| Quarter | Q4 |
| Day Name | Tuesday |

### Join Types Quick Reference
| Join Type | Keeps Records From |
|-----------|-------------------|
| Left Outer | All from left table |
| Right Outer | All from right table |
| Inner | Only matching records |
| Full Outer | All from both tables |
| Left Anti | Left only (no match) |
| Right Anti | Right only (no match) |

### Conditional Operators
| Operator | Best For |
|----------|----------|
| equals | Exact match |
| greater than | Numeric thresholds |
| contains | Text search |
| begins with | Prefix matching |
| ends with | Suffix matching |

---

**End of Guide**
