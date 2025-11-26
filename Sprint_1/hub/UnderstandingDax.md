# Power BI DAX - Practical Step-by-Step Guide

## Table of Contents
1. [DAX Syntax Basics](#1-dax-syntax-basics)
2. [Common DAX Functions](#2-common-dax-functions)
3. [Creating Calculated Columns - Step by Step](#3-creating-calculated-columns-step-by-step)
4. [Creating Measures - Step by Step](#4-creating-measures-step-by-step)
5. [Calculated Columns vs Measures](#5-calculated-columns-vs-measures)
6. [Practice Exercises](#6-practice-exercises)

---

## 1. DAX Syntax Basics

### What is DAX?
**DAX = Data Analysis Expressions** - Formula language for Power BI calculations

### Basic Formula Structure:
```dax
Name = FUNCTION(Table[Column])
```

### Key Rules:
- Always start with `=`
- Use `Table[Column]` format
- Use `'Table Name'[Column]` if table name has spaces
- Functions are UPPERCASE (e.g., SUM, AVERAGE)
- Use `&` for text concatenation
- Comments start with `//`

### Example:
```dax
Total Sales = SUM(Sales[Amount])
```

---

## 2. Common DAX Functions

### SUM() - Add Numbers
```dax
Total Sales = SUM(Sales[Amount])
Total Quantity = SUM(Orders[Quantity])
```

### AVERAGE() - Calculate Mean
```dax
Average Sale = AVERAGE(Sales[Amount])
Avg Price = AVERAGE(Products[Price])
```

### COUNT() - Count Non-Blank Values
```dax
Order Count = COUNT(Orders[OrderID])
```

### COUNTROWS() - Count All Rows (Most Reliable)
```dax
Total Orders = COUNTROWS(Orders)
Unique Customers = COUNTROWS(DISTINCT(Sales[CustomerID]))
```

### Quick Comparison:

| Function | Use For |
|----------|---------|
| **SUM** | Total sales, revenue, quantities |
| **AVERAGE** | Average price, ratings, amounts |
| **COUNT** | Count specific column values |
| **COUNTROWS** | Count records (recommended) |

---

## 3. Creating Calculated Columns - Step by Step

### What is a Calculated Column?
- New column added to your table
- Calculated row-by-row
- Stored in memory
- Visible in Data View

---

### Step-by-Step: Create Your First Calculated Column

#### Step 1: Open Power BI and Load Data
1. Open **Power BI Desktop**
2. Click **Get Data** → Choose your source (Excel, CSV, etc.)
3. Load your data
4. Click **Close & Apply**

#### Step 2: Switch to Data View
1. On the left sidebar, click the **Data icon** (looks like a table)
2. You'll see your tables listed on the right
3. Select the table where you want to add a column

#### Step 3: Create New Column
1. Look at the top ribbon
2. Click **"Modeling"** tab
3. Click **"New Column"** button
4. Formula bar appears at the top

#### Step 4: Write Your Formula
Type in the formula bar:
```dax
Column Name = Your Formula
```

#### Step 5: Press Enter
- Column is created instantly
- Scroll right in your table to see it
- Values are calculated for all rows

---

### Practical Examples with Screenshots Guide

#### Example 1: Calculate Line Total

**Formula:**
```dax
Line Total = Sales[Quantity] * Sales[UnitPrice]
```

**Steps:**
1. Data View → Select "Sales" table
2. Modeling Tab → New Column
3. Type: `Line Total = Sales[Quantity] * Sales[UnitPrice]`
4. Press Enter
5. ✅ New column appears with calculated values

---

#### Example 2: Extract Year from Date

**Formula:**
```dax
Order Year = YEAR(Orders[OrderDate])
```

**Steps:**
1. Data View → Select "Orders" table
2. Modeling Tab → New Column
3. Type: `Order Year = YEAR(Orders[OrderDate])`
4. Press Enter
5. ✅ New column shows year (e.g., 2024)

---

#### Example 3: Create Categories

**Formula:**
```dax
Sales Category = 
IF(
    Sales[Amount] > 5000, 
    "High",
    IF(Sales[Amount] > 1000, "Medium", "Low")
)
```

**Steps:**
1. Data View → Select "Sales" table
2. Modeling Tab → New Column
3. Type the formula above
4. Press Enter
5. ✅ New column shows: High, Medium, or Low

---

#### Example 4: Combine Text Fields

**Formula:**
```dax
Full Name = Customers[FirstName] & " " & Customers[LastName]
```

**Steps:**
1. Data View → Select "Customers" table
2. Modeling Tab → New Column
3. Type: `Full Name = Customers[FirstName] & " " & Customers[LastName]`
4. Press Enter
5. ✅ New column shows full names

---

#### Example 5: Get Related Data

**Formula:**
```dax
Product Category = RELATED(Products[Category])
```

**Steps:**
1. Data View → Select "Sales" table (must have relationship to Products)
2. Modeling Tab → New Column
3. Type: `Product Category = RELATED(Products[Category])`
4. Press Enter
5. ✅ New column brings category from Products table

---

### 10 Quick Calculated Column Formulas

```dax
// 1. Calculate profit
Profit = Sales[Revenue] - Sales[Cost]

// 2. Month name
Month Name = FORMAT(Orders[OrderDate], "MMMM")

// 3. Quarter
Quarter = "Q" & QUARTER(Orders[OrderDate])

// 4. Age calculation
Age = DATEDIFF(Customers[BirthDate], TODAY(), YEAR)

// 5. Discount amount
Discount = Sales[LineTotal] * 0.10

// 6. Round to 2 decimals
Rounded Sales = ROUND(Sales[Amount], 2)

// 7. Uppercase text
Product Upper = UPPER(Products[ProductName])

// 8. Email creation
Email = LOWER(Customers[FirstName]) & "@company.com"

// 9. Simple flag
High Value = IF(Sales[Amount] > 10000, "Yes", "No")

// 10. Weekend check
Is Weekend = IF(WEEKDAY(Orders[OrderDate]) IN {1, 7}, "Yes", "No")
```

---

## 4. Creating Measures - Step by Step

### What is a Measure?
- Dynamic calculation
- NOT stored (calculated on demand)
- Responds to filters and slicers
- Shows only in visuals, not in tables

---

### Step-by-Step: Create Your First Measure

#### Step 1: Switch to Report View
1. On the left sidebar, click the **Report icon** (first icon - looks like a bar chart)
2. You'll see your blank canvas

#### Step 2: Create New Measure
**Method 1 - From Fields Pane:**
1. Look at **Fields pane** on the right
2. Right-click on your table name (e.g., "Sales")
3. Select **"New Measure"**
4. Formula bar appears

**Method 2 - From Ribbon:**
1. Click **"Modeling"** tab
2. Click **"New Measure"** button
3. Formula bar appears

#### Step 3: Write Your Formula
Type in the formula bar:
```dax
Measure Name = FUNCTION(Table[Column])
```

#### Step 4: Press Enter
- Measure is created
- Shows in Fields pane with calculator icon 🧮
- Won't see it in Data View (measures don't show there)

#### Step 5: Use in Visual
1. Drag a visual to canvas (e.g., Card or Table)
2. Drag your measure into the visual
3. ✅ See the result!

---

### Practical Measure Examples

#### Example 1: Total Sales (Most Common)

**Formula:**
```dax
Total Sales = SUM(Sales[Amount])
```

**Steps:**
1. Report View
2. Right-click "Sales" table → New Measure
3. Type: `Total Sales = SUM(Sales[Amount])`
4. Press Enter
5. **Test it:**
   - Add a **Card visual** to canvas
   - Drag "Total Sales" measure to the card
   - ✅ See the total!

---

#### Example 2: Average Order Value

**Formula:**
```dax
Average Order Value = AVERAGE(Sales[Amount])
```

**Steps:**
1. Right-click "Sales" table → New Measure
2. Type: `Average Order Value = AVERAGE(Sales[Amount])`
3. Press Enter
4. **Test it:**
   - Add Card visual
   - Drag measure to card
   - ✅ See average!

---

#### Example 3: Count of Orders

**Formula:**
```dax
Total Orders = COUNTROWS(Orders)
```

**Steps:**
1. Right-click "Orders" table → New Measure
2. Type: `Total Orders = COUNTROWS(Orders)`
3. Press Enter
4. **Test it:**
   - Add Card visual
   - Drag measure to card
   - ✅ See count!

---

#### Example 4: Unique Customer Count

**Formula:**
```dax
Unique Customers = DISTINCTCOUNT(Sales[CustomerID])
```

**Steps:**
1. Right-click "Sales" table → New Measure
2. Type: `Unique Customers = DISTINCTCOUNT(Sales[CustomerID])`
3. Press Enter
4. ✅ Shows unique customer count

---

#### Example 5: Profit Margin Percentage

**Formula:**
```dax
Profit Margin % = 
DIVIDE(
    SUM(Sales[Profit]),
    SUM(Sales[Revenue]),
    0
) * 100
```

**Steps:**
1. Right-click "Sales" table → New Measure
2. Type the formula above
3. Press Enter
4. **Format as percentage:**
   - Select the measure in Fields pane
   - Modeling tab → Format → Percentage
   - Set decimal places to 2

---

### Testing Your Measures with Slicers

**To see measures respond to filters:**

1. **Create a measure:**
   ```dax
   Total Sales = SUM(Sales[Amount])
   ```

2. **Add visuals:**
   - Add a **Card visual** with your measure
   - Add a **Slicer** (Insert → Slicer)
   - Add "Year" or "Region" to the slicer

3. **Test it:**
   - Click different values in slicer
   - ✅ Watch the measure update automatically!

---

### 10 Essential Measures

```dax
// 1. Total revenue
Total Revenue = SUM(Sales[Revenue])

// 2. Total cost
Total Cost = SUM(Sales[Cost])

// 3. Total profit
Total Profit = [Total Revenue] - [Total Cost]

// 4. Average sale
Average Sale = AVERAGE(Sales[Amount])

// 5. Order count
Order Count = COUNTROWS(Orders)

// 6. Unique products
Unique Products = DISTINCTCOUNT(Sales[ProductID])

// 7. Sales per customer
Sales Per Customer = DIVIDE([Total Sales], [Unique Customers], 0)

// 8. Max sale
Maximum Sale = MAX(Sales[Amount])

// 9. Min sale
Minimum Sale = MIN(Sales[Amount])

// 10. Profit margin
Profit Margin = DIVIDE([Total Profit], [Total Revenue], 0)
```

---

## 5. Calculated Columns vs Measures

### Quick Comparison

| Aspect | Calculated Column | Measure |
|--------|-------------------|---------|
| **Icon** | 📊 Column | 🧮 Calculator |
| **Where to create** | Data View | Report View |
| **Storage** | Stored in table | Not stored |
| **When calculated** | At refresh | When used |
| **Visible in table** | ✅ Yes | ❌ No |
| **Use in slicers** | ✅ Yes | ❌ No |
| **Responds to filters** | ❌ No | ✅ Yes |
| **Memory usage** | ⚠️ High | ✅ Low |
| **Best for** | Categories, row calculations | Totals, KPIs |

---

### When to Use What?

#### Use Calculated Column For:
✅ Creating categories: High/Medium/Low
✅ Extracting date parts: Year, Month, Quarter
✅ Combining text: First Name + Last Name
✅ Row-level math: Quantity × Price
✅ Lookups: RELATED(Products[Category])

#### Use Measure For:
✅ Totals: Total Sales, Total Revenue
✅ Averages: Average Order Value
✅ Counts: Number of Orders
✅ Percentages: Profit Margin %
✅ Any KPI for dashboard

---

### Visual Test: Column vs Measure

#### Test 1: Can You Use It in a Slicer?
- **Calculated Column:** ✅ YES
- **Measure:** ❌ NO

#### Test 2: Does It Show in Data View?
- **Calculated Column:** ✅ YES
- **Measure:** ❌ NO

#### Test 3: Does It Change with Filters?
- **Calculated Column:** ❌ NO (values are fixed)
- **Measure:** ✅ YES (recalculates)

---

## 6. Practice Exercises

### Exercise Set 1: Calculated Columns

**Scenario:** You have a Sales table with: OrderDate, Product, Quantity, UnitPrice, Region

**Create these calculated columns:**

```dax
// 1. Line total
Line Total = Sales[Quantity] * Sales[UnitPrice]

// 2. Year
Order Year = YEAR(Sales[OrderDate])

// 3. Month name
Month Name = FORMAT(Sales[OrderDate], "MMMM")

// 4. Sales size
Sales Size = IF(Sales[Line Total] > 1000, "Large", "Small")

// 5. Quarter
Quarter Number = QUARTER(Sales[OrderDate])
```

**How to test:**
1. Create each column in Data View
2. Scroll right to see new columns
3. Verify values make sense

---

### Exercise Set 2: Basic Measures

**Create these measures:**

```dax
// 1. Total sales
Total Sales = SUM(Sales[LineTotal])

// 2. Average order
Average Order = AVERAGE(Sales[LineTotal])

// 3. Order count
Total Orders = COUNTROWS(Sales)

// 4. Total quantity
Total Quantity Sold = SUM(Sales[Quantity])

// 5. Average quantity
Avg Quantity Per Order = AVERAGE(Sales[Quantity])
```

**How to test:**
1. Create each measure in Report View
2. Add 5 Card visuals to canvas
3. Put one measure in each card
4. ✅ All should show numbers

---

### Exercise Set 3: Measures with Filters

**Create dashboard to test filter context:**

**Step 1: Create Measures**
```dax
Total Sales = SUM(Sales[LineTotal])
Order Count = COUNTROWS(Sales)
Average Sale = AVERAGE(Sales[LineTotal])
```

**Step 2: Create Visuals**
1. Add 3 **Card visuals** with the 3 measures
2. Add a **Slicer** → Use "Year" or "Region"
3. Add a **Table visual** → Show Product, Total Sales

**Step 3: Test**
1. Change slicer selection
2. ✅ Watch all measures update automatically
3. ✅ See how measures respond to filters

---

### Exercise Set 4: Combining Measures

**Create calculated measures:**

```dax
// Base measures
Total Revenue = SUM(Sales[Revenue])
Total Cost = SUM(Sales[Cost])

// Calculated from other measures
Total Profit = [Total Revenue] - [Total Cost]

Profit Margin % = 
DIVIDE(
    [Total Profit],
    [Total Revenue],
    0
) * 100

Sales Per Order = 
DIVIDE(
    [Total Revenue],
    COUNTROWS(Orders),
    0
)
```

**Test with visual:**
1. Create a **Table visual**
2. Add: Region (rows)
3. Add: Total Revenue, Total Profit, Profit Margin %
4. ✅ See calculations by region

---

### Exercise Set 5: Complete Dashboard

**Build a mini sales dashboard:**

**Step 1: Create Measures**
```dax
Total Sales = SUM(Sales[Amount])
Total Orders = COUNTROWS(Orders)
Avg Order Value = DIVIDE([Total Sales], [Total Orders], 0)
Unique Customers = DISTINCTCOUNT(Sales[CustomerID])
```

**Step 2: Create Calculated Columns**
```dax
Year = YEAR(Sales[OrderDate])
Month = FORMAT(Sales[OrderDate], "MMM")
Sales Category = IF(Sales[Amount] > 5000, "High", "Low")
```

**Step 3: Build Dashboard**
1. Add 4 **Cards** at top with measures
2. Add **Slicer** for Year
3. Add **Clustered Bar Chart**: Month (axis) × Total Sales (values)
4. Add **Pie Chart**: Sales Category × Total Sales
5. Add **Table**: Product, Total Sales, Total Orders

**Step 4: Test**
1. Change year in slicer
2. ✅ Everything updates automatically
3. Click on bar chart
4. ✅ Cross-filtering works!

---

## Quick Reference Guide

### Creating Calculated Column
1. **Data View** → Select table
2. **Modeling tab** → **New Column**
3. Type: `Name = Formula`
4. Press **Enter**

### Creating Measure
1. **Report View** → Right-click table
2. **New Measure**
3. Type: `Name = Formula`
4. Press **Enter**

### Common Functions Quick List

```dax
// Aggregation
SUM(Table[Column])
AVERAGE(Table[Column])
COUNT(Table[Column])
COUNTROWS(Table)
MIN(Table[Column])
MAX(Table[Column])
DISTINCTCOUNT(Table[Column])

// Date
YEAR(Date)
MONTH(Date)
QUARTER(Date)
FORMAT(Date, "MMMM")
TODAY()
DATEDIFF(StartDate, EndDate, DAY)

// Text
UPPER(Text)
LOWER(Text)
CONCATENATE(Text1, Text2) or Text1 & Text2
LEFT(Text, NumChars)
RIGHT(Text, NumChars)
LEN(Text)

// Logical
IF(Condition, TrueValue, FalseValue)
SWITCH(Expression, Value1, Result1, Value2, Result2, DefaultResult)
AND(Condition1, Condition2)
OR(Condition1, Condition2)

// Math
ROUND(Number, Decimals)
DIVIDE(Numerator, Denominator, AlternateResult)
ABS(Number)
POWER(Number, Power)
SQRT(Number)

// Relationships
RELATED(RelatedTable[Column])
RELATEDTABLE(Table)
```

---

## Troubleshooting Common Errors

### Error: "A single value for column cannot be determined"
**Problem:** Using aggregation in calculated column
```dax
// ❌ Wrong
Total = SUM(Sales[Amount])

// ✅ Right - Use measure instead
Total Sales = SUM(Sales[Amount])
```

### Error: "Column 'X' in table 'Y' cannot be found"
**Problem:** Typo in table or column name
```dax
// ❌ Wrong
Sales[Amout]

// ✅ Right
Sales[Amount]
```

### Error: "Calculation error"
**Problem:** Division by zero
```dax
// ❌ Wrong
Margin = Sales[Profit] / Sales[Revenue]

// ✅ Right - Use DIVIDE
Margin = DIVIDE(Sales[Profit], Sales[Revenue], 0)
```

---

## Next Steps

1. ✅ Practice creating 5 calculated columns
2. ✅ Practice creating 5 measures
3. ✅ Build a simple dashboard
4. ✅ Test measures with slicers
5. ✅ Learn time intelligence functions (TOTALYTD, SAMEPERIODLASTYEAR)
6. ✅ Explore CALCULATE function for advanced filtering

---

## Summary

### Key Takeaways:
- **Calculated Columns** = Row-by-row calculations, stored in table
- **Measures** = Aggregations, calculated on demand
- Use **Data View** for columns, **Report View** for measures
- Always test with visuals and filters
- Start simple, then build complexity
- Measures are preferred for most KPIs

### Remember:
- `SUM` for totals
- `AVERAGE` for means
- `COUNTROWS` for counts (most reliable)
- `DIVIDE` to avoid division errors
- Measures respond to filters, columns don't

**Now go practice! The more you practice, the better you'll get! 🚀**

