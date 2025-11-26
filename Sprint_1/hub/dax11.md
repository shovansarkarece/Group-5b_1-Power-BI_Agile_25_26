# Complete DAX Guide for Power BI - From Basics to Practice

## Table of Contents
1. [Understanding DAX Syntax and Formula Structure](#1-understanding-dax-syntax-and-formula-structure)
2. [Common DAX Functions: SUM, AVERAGE, COUNT, COUNTROWS](#2-common-dax-functions)
3. [Creating Calculated Columns Using DAX](#3-creating-calculated-columns-using-dax)
4. [Difference Between Calculated Columns and Measures](#4-calculated-columns-vs-measures)
5. [Practice Exercises with Sample Dataset](#5-practice-exercises-with-sample-dataset)
6. [Advanced DAX Concepts](#6-advanced-dax-concepts)
7. [Common Mistakes and Solutions](#7-common-mistakes-and-solutions)
8. [Quick Reference Guide](#8-quick-reference-guide)

---

## 1. Understanding DAX Syntax and Formula Structure

### What is DAX?

**DAX = Data Analysis Expressions**

DAX is a formula language used in Power BI, Power Pivot, and Analysis Services. It's designed to work with relational data and perform dynamic aggregation and calculations.

**Key Characteristics:**
- Similar to Excel formulas but more powerful
- Works with tables and columns, not just cells
- Context-aware (understands filters and relationships)
- Optimized for large datasets

---

### Basic DAX Syntax Structure

#### Standard Formula Pattern:
```dax
Name = FUNCTION(Table[Column])
```

#### Components Breakdown:

**1. Name (Left Side of =)**
- What you're creating (measure or calculated column)
- Must be unique within the table
- Can contain spaces but better without
- Case-sensitive

**2. Equals Sign (=)**
- Always required
- Separates name from formula

**3. Function**
- Built-in DAX function (SUM, AVERAGE, IF, etc.)
- Can be nested
- Case-insensitive but conventionally UPPERCASE

**4. Table[Column] Reference**
- Table name followed by column in square brackets
- Use single quotes for table names with spaces: 'Sales Data'[Amount]
- Column names are case-sensitive

---

### DAX Syntax Rules

#### Rule 1: Table and Column References
```dax
// Correct
Sales[Amount]
'Sales Data'[Amount]

// Incorrect
Sales.Amount
SalesAmount
[Amount]  // Missing table reference in calculated columns
```

#### Rule 2: Operators
```dax
// Arithmetic Operators
+  // Addition
-  // Subtraction
*  // Multiplication
/  // Division
^  // Exponentiation

// Comparison Operators
=   // Equals
<>  // Not equal
>   // Greater than
<   // Less than
>=  // Greater than or equal
<=  // Less than or equal

// Logical Operators
&&  // AND
||  // OR
!   // NOT

// Text Operator
&   // Concatenation
```

#### Rule 3: Data Types
```dax
// Numeric
1234
1234.56

// Text (must use quotes)
"Hello"
"Product A"

// Boolean
TRUE
FALSE

// Date/Time
DATE(2024, 11, 26)
TODAY()
NOW()
```

---

### Basic Formula Examples

#### Example 1: Simple Calculation
```dax
Total Sales = SUM(Sales[Amount])
```
**Explanation:**
- Name: "Total Sales"
- Function: SUM
- Reference: Sales table, Amount column

#### Example 2: Mathematical Operation
```dax
Profit = Sales[Revenue] - Sales[Cost]
```
**Explanation:**
- Subtracts Cost from Revenue for each row
- Works in calculated columns

#### Example 3: Text Concatenation
```dax
Full Name = Customers[FirstName] & " " & Customers[LastName]
```
**Explanation:**
- Combines first name, space, and last name
- Uses & operator for text

#### Example 4: Conditional Logic
```dax
Status = IF(Sales[Amount] > 1000, "High", "Low")
```
**Explanation:**
- IF function checks condition
- Returns "High" if true, "Low" if false

---

### Formula Structure Patterns

#### Pattern 1: Single Function
```dax
Measure Name = FUNCTION(Table[Column])
```
Example:
```dax
Total Revenue = SUM(Sales[Revenue])
```

#### Pattern 2: Multiple Functions (Nested)
```dax
Measure Name = FUNCTION1(FUNCTION2(Table[Column]))
```
Example:
```dax
Average Rounded = ROUND(AVERAGE(Sales[Amount]), 2)
```

#### Pattern 3: Column Calculations
```dax
Column Name = Table[Column1] operator Table[Column2]
```
Example:
```dax
Line Total = Sales[Quantity] * Sales[UnitPrice]
```

#### Pattern 4: Conditional Logic
```dax
Result = IF(condition, value_if_true, value_if_false)
```
Example:
```dax
Category = IF(Sales[Amount] > 5000, "Premium", "Standard")
```

#### Pattern 5: Complex Calculations
```dax
Measure = FUNCTION1(expression1) operator FUNCTION2(expression2)
```
Example:
```dax
Profit Margin = DIVIDE(SUM(Sales[Profit]), SUM(Sales[Revenue]))
```

---

### Understanding Context

DAX operates in two types of context:

#### Row Context
- Applies to calculated columns
- Evaluates formula row by row
- Each row is evaluated independently

Example:
```dax
// This runs for EACH row
Profit Per Item = Sales[Revenue] - Sales[Cost]
```

#### Filter Context
- Applies to measures
- Considers all active filters (slicers, visuals, etc.)
- Aggregates across filtered data

Example:
```dax
// This aggregates based on current filters
Total Sales = SUM(Sales[Amount])
```

---

### Comments in DAX

Use comments to document your formulas:

```dax
// Single-line comment
Total Sales = SUM(Sales[Amount])  // Sums all sales amounts

/* 
Multi-line comment
This measure calculates total revenue
across all filtered sales records
*/
Total Revenue = SUM(Sales[Revenue])
```

---

### Best Practices for DAX Syntax

✅ **Do:**
- Use descriptive names (e.g., "Total Sales YTD" not "TS")
- Keep formulas readable with line breaks in complex calculations
- Use comments for complex logic
- Follow consistent naming conventions
- Test formulas with small datasets first

❌ **Don't:**
- Use spaces in table/column names (use underscores instead)
- Create circular references
- Mix aggregations incorrectly
- Forget table references in calculated columns
- Use reserved keywords as names

---

## 2. Common DAX Functions

### The Essential Four Functions

---

### 2.1 SUM() Function

#### Purpose
Adds all numbers in a column.

#### Syntax
```dax
SUM(Table[Column])
```

#### Parameters
- **Column**: A column containing numeric values

#### Return Value
- Decimal number (sum of all values)

#### Behavior
- Ignores blank cells
- Ignores text and boolean values
- Returns 0 if no numeric values found

#### Examples

**Example 1: Basic Sum**
```dax
Total Sales = SUM(Sales[Amount])
```

**Example 2: Sum with Multiple Columns**
```dax
Total Revenue = SUM(Sales[Revenue])
Total Cost = SUM(Sales[Cost])
Total Profit = [Total Revenue] - [Total Cost]
```

**Example 3: Sum in Calculated Column** (Not recommended)
```dax
// This would sum ALL rows, not ideal for calculated columns
Total All Sales = SUM(Sales[Amount])  // Use SUMX for row context
```

#### When to Use
- ✅ Calculating total sales/revenue
- ✅ Summing quantities sold
- ✅ Aggregating amounts
- ✅ KPI totals in dashboards

#### Common Mistakes
```dax
// Wrong - Missing table reference
Total = SUM([Amount])

// Wrong - Using on text column
Total Names = SUM(Customers[Name])  // Error!

// Correct
Total Sales = SUM(Sales[Amount])
```

---

### 2.2 AVERAGE() Function

#### Purpose
Calculates the arithmetic mean of numbers in a column.

#### Syntax
```dax
AVERAGE(Table[Column])
```

#### Parameters
- **Column**: A column containing numeric values

#### Return Value
- Decimal number (average of all values)

#### Behavior
- Ignores blank cells
- Ignores text and boolean values
- Counts only cells with numbers
- Returns blank if no numeric values

#### Examples

**Example 1: Basic Average**
```dax
Average Sale = AVERAGE(Sales[Amount])
```

**Example 2: Average Price**
```dax
Avg Unit Price = AVERAGE(Products[UnitPrice])
```

**Example 3: Average with Conditions**
```dax
Avg High Value Sales = 
CALCULATE(
    AVERAGE(Sales[Amount]),
    Sales[Amount] > 1000
)
```

#### Related Functions

**AVERAGEA()** - Includes text and boolean values
```dax
Avg Including Text = AVERAGEA(Sales[Amount])
```

**AVERAGEX()** - Row-by-row average with expression
```dax
Avg Profit = AVERAGEX(Sales, Sales[Revenue] - Sales[Cost])
```

#### When to Use
- ✅ Average order value
- ✅ Mean price calculation
- ✅ Average rating/score
- ✅ Performance metrics

#### Common Pitfalls
```dax
// Be aware: Average ignores blanks
// If you have: 100, 200, blank, 300
Average = AVERAGE(Sales[Amount])  // Result: 200 (not 150)

// To include zeros:
Average With Zeros = AVERAGEX(Sales, Sales[Amount] + 0)
```

---

### 2.3 COUNT() Function

#### Purpose
Counts the number of cells containing non-blank values.

#### Syntax
```dax
COUNT(Table[Column])
```

#### Parameters
- **Column**: A column of any data type

#### Return Value
- Whole number (count of non-blank cells)

#### Behavior
- Counts only non-blank values
- Counts numbers, dates, text
- Does NOT count blank cells
- Does NOT count errors

#### Examples

**Example 1: Basic Count**
```dax
Order Count = COUNT(Orders[OrderID])
```

**Example 2: Count Products**
```dax
Product Count = COUNT(Products[ProductName])
```

**Example 3: Count Non-Blank Values**
```dax
Completed Orders = COUNT(Orders[CompletionDate])
```

#### Related Functions

**COUNTA()** - Counts all non-blank values (including text)
```dax
Count All Values = COUNTA(Sales[Status])
```

**COUNTBLANK()** - Counts blank cells
```dax
Missing Values = COUNTBLANK(Sales[ShipDate])
```

**DISTINCTCOUNT()** - Counts unique values
```dax
Unique Customers = DISTINCTCOUNT(Sales[CustomerID])
```

#### When to Use
- ✅ Count of orders/transactions
- ✅ Count of completed items
- ✅ Number of entries
- ⚠️ Use COUNTROWS() for more reliable record counts

#### Important Notes
```dax
// COUNT may miss rows if column has blanks
Orders Count = COUNT(Orders[OrderID])  // Might miss some

// COUNTROWS is more reliable
Orders Count = COUNTROWS(Orders)  // Counts ALL rows
```

---

### 2.4 COUNTROWS() Function

#### Purpose
Counts the number of rows in a table or table expression.

#### Syntax
```dax
COUNTROWS(Table)
```

#### Parameters
- **Table**: A table or table expression

#### Return Value
- Whole number (count of rows)

#### Behavior
- Counts ALL rows (including blanks)
- More reliable than COUNT()
- Works with filtered tables
- Can be used with virtual tables

#### Examples

**Example 1: Basic Row Count**
```dax
Total Orders = COUNTROWS(Orders)
```

**Example 2: Count with Filter**
```dax
High Value Orders = 
COUNTROWS(
    FILTER(Orders, Orders[Amount] > 1000)
)
```

**Example 3: Count Distinct Values**
```dax
Unique Customers = 
COUNTROWS(
    DISTINCT(Sales[CustomerID])
)
```

**Example 4: Count in Related Table**
```dax
Orders Per Customer = 
COUNTROWS(
    RELATEDTABLE(Orders)
)
```

#### COUNTROWS vs COUNT

| Aspect | COUNTROWS | COUNT |
|--------|-----------|-------|
| **Counts** | All rows | Non-blank values |
| **Reliability** | More reliable | May miss rows |
| **Use with** | Tables | Columns |
| **Performance** | Better | Slightly slower |
| **Recommendation** | Preferred | Use for specific needs |

#### When to Use
- ✅ **Always** for counting records (most reliable)
- ✅ Counting filtered rows
- ✅ Counting related records
- ✅ Counting distinct groups

#### Best Practice Examples
```dax
// ✅ Recommended
Total Records = COUNTROWS(Sales)

// ⚠️ Less reliable (might miss rows if OrderID is blank)
Total Records = COUNT(Sales[OrderID])

// ✅ Count distinct
Unique Products = COUNTROWS(DISTINCT(Sales[ProductID]))

// ✅ Count with multiple filters
High Value North Sales = 
COUNTROWS(
    FILTER(
        Sales,
        Sales[Amount] > 1000 && Sales[Region] = "North"
    )
)
```

---

### Function Comparison Table

| Function | Counts/Calculates | Blank Values | Data Type | Best Use Case |
|----------|-------------------|--------------|-----------|---------------|
| **SUM()** | Sum of numbers | Ignored | Numeric only | Total sales, revenue |
| **AVERAGE()** | Mean of numbers | Ignored | Numeric only | Average price, rating |
| **COUNT()** | Non-blank values | Ignored | Any type | Count non-empty cells |
| **COUNTROWS()** | All rows | Included | N/A (table) | Reliable row count |

---

### Additional Common Functions

#### DIVIDE() - Safe Division
```dax
// Prevents divide-by-zero errors
Profit Margin = DIVIDE(SUM(Sales[Profit]), SUM(Sales[Revenue]), 0)
//                                                                  ^ alternate result if division by zero
```

#### MIN() and MAX()
```dax
Lowest Price = MIN(Products[Price])
Highest Price = MAX(Products[Price])
```

#### DISTINCTCOUNT()
```dax
Unique Customers = DISTINCTCOUNT(Sales[CustomerID])
```

#### CONCATENATE() or & Operator
```dax
Full Address = Customers[Street] & ", " & Customers[City]
```

---

## 3. Creating Calculated Columns Using DAX

### What are Calculated Columns?

**Definition:**
Calculated columns are new columns added to your tables using DAX formulas. They are computed row-by-row and stored in your data model.

**Characteristics:**
- ✅ Evaluated when data loads/refreshes
- ✅ Stored in memory (permanent)
- ✅ Visible in Data View
- ✅ Can be used in rows, columns, filters, and slicers
- ✅ Calculated in row context
- ⚠️ Takes up memory space

---

### How to Create Calculated Columns

#### Method 1: Using Data View (Recommended)

**Step 1: Switch to Data View**
1. Open Power BI Desktop
2. Click **Data icon** (table icon) on the left sidebar
3. Select the table where you want to add the column

**Step 2: Create New Column**
1. Click **"Table tools"** or **"Modeling"** tab in the ribbon
2. Click **"New Column"** button
3. Formula bar appears at the top

**Step 3: Write DAX Formula**
```dax
Column Name = Your Formula Here
```

**Step 4: Press Enter**
- Column is created immediately
- Values are calculated for all rows
- Column appears in your table

#### Method 2: Using Modeling Tab

1. Go to any view (Report, Data, or Model)
2. Select **"Modeling"** tab
3. Click **"New Column"**
4. Type your formula
5. Press Enter

---

### Basic Calculated Column Examples

#### Example 1: Mathematical Operations

**Scenario: Calculate Line Total**
```dax
Line Total = Sales[Quantity] * Sales[UnitPrice]
```

**Scenario: Calculate Profit**
```dax
Profit = Sales[Revenue] - Sales[Cost]
```

**Scenario: Calculate Discount Amount**
```dax
Discount Amount = Sales[LineTotal] * Sales[DiscountPercent]
```

**Scenario: Calculate Net Amount**
```dax
Net Amount = Sales[LineTotal] - Sales[DiscountAmount]
```

---

#### Example 2: Text Operations

**Scenario: Combine First and Last Name**
```dax
Full Name = Customers[FirstName] & " " & Customers[LastName]
```

**Scenario: Create Email Address**
```dax
Email = LOWER(Customers[FirstName]) & "." & LOWER(Customers[LastName]) & "@company.com"
```

**Scenario: Extract Initials**
```dax
Initials = LEFT(Customers[FirstName], 1) & LEFT(Customers[LastName], 1)
```

**Scenario: Create Full Address**
```dax
Full Address = 
    Customers[Street] & ", " & 
    Customers[City] & ", " & 
    Customers[State] & " " & 
    Customers[ZipCode]
```

---

#### Example 3: Date Extractions

**Scenario: Extract Year**
```dax
Order Year = YEAR(Orders[OrderDate])
```

**Scenario: Extract Month Number**
```dax
Order Month = MONTH(Orders[OrderDate])
```

**Scenario: Extract Month Name**
```dax
Month Name = FORMAT(Orders[OrderDate], "MMMM")
```

**Scenario: Extract Quarter**
```dax
Quarter = "Q" & QUARTER(Orders[OrderDate])
```

**Scenario: Extract Day of Week**
```dax
Day Name = FORMAT(Orders[OrderDate], "dddd")
```

**Scenario: Get Week Number**
```dax
Week Number = WEEKNUM(Orders[OrderDate])
```

**Scenario: Calculate Age from Birth Date**
```dax
Age = DATEDIFF(Customers[BirthDate], TODAY(), YEAR)
```

---

#### Example 4: Conditional Logic (IF Statements)

**Scenario: Simple Category**
```dax
Sales Category = 
IF(
    Sales[Amount] > 1000,
    "High",
    "Low"
)
```

**Scenario: Three-Tier Category**
```dax
Sales Category = 
IF(
    Sales[Amount] > 5000,
    "High",
    IF(
        Sales[Amount] > 1000,
        "Medium",
        "Low"
    )
)
```

**Scenario: Status Based on Date**
```dax
Order Status = 
IF(
    Orders[ShipDate] <= Orders[DueDate],
    "On Time",
    "Late"
)
```

**Scenario: Age Group Classification**
```dax
Age Group = 
IF(
    Customers[Age] < 18,
    "Minor",
    IF(
        Customers[Age] < 30,
        "Young Adult",
        IF(
            Customers[Age] < 50,
            "Adult",
            IF(
                Customers[Age] < 65,
                "Middle Aged",
                "Senior"
            )
        )
    )
)
```

---

#### Example 5: SWITCH Statement (Better than Nested IFs)

**Scenario: Convert Month Number to Season**
```dax
Season = 
SWITCH(
    MONTH(Orders[OrderDate]),
    12, "Winter",
    1, "Winter",
    2, "Winter",
    3, "Spring",
    4, "Spring",
    5, "Spring",
    6, "Summer",
    7, "Summer",
    8, "Summer",
    9, "Fall",
    10, "Fall",
    11, "Fall",
    "Unknown"
)
```

**Scenario: Product Category Mapping**
```dax
Category Name = 
SWITCH(
    Products[CategoryCode],
    "A", "Electronics",
    "B", "Clothing",
    "C", "Food",
    "D", "Books",
    "Other"
)
```

**Scenario: Priority Level**
```dax
Priority = 
SWITCH(
    TRUE(),
    Orders[Amount] > 10000, "Critical",
    Orders[Amount] > 5000, "High",
    Orders[Amount] > 1000, "Medium",
    "Low"
)
```

---

#### Example 6: Using RELATED() Function

**Purpose:** Access columns from related tables

**Scenario: Get Customer Name in Orders Table**
```dax
Customer Name = RELATED(Customers[CustomerName])
```

**Scenario: Get Product Category in Sales Table**
```dax
Product Category = RELATED(Products[Category])
```

**Scenario: Get Product Price in Orders Table**
```dax
Unit Price = RELATED(Products[Price])
```

**Scenario: Calculate Extended Price Using Related Table**
```dax
Extended Price = Orders[Quantity] * RELATED(Products[Price])
```

---

#### Example 7: Mathematical Functions

**Scenario: Round to 2 Decimals**
```dax
Rounded Sales = ROUND(Sales[Amount], 2)
```

**Scenario: Calculate Percentage**
```dax
Profit Margin % = 
DIVIDE(
    Sales[Profit],
    Sales[Revenue],
    0
) * 100
```

**Scenario: Absolute Value**
```dax
Absolute Variance = ABS(Sales[Actual] - Sales[Budget])
```

**Scenario: Calculate Tax**
```dax
Tax Amount = Sales[LineTotal] * 0.08
Total With Tax = Sales[LineTotal] * 1.08
```

**Scenario: Power Calculation**
```dax
Squared Value = POWER(Sales[Amount], 2)
Square Root = SQRT(Sales[Amount])
```

---

#### Example 8: Text Functions

**Scenario: Uppercase Conversion**
```dax
Product Name Upper = UPPER(Products[ProductName])
```

**Scenario: Lowercase Conversion**
```dax
Email Lower = LOWER(Customers[Email])
```

**Scenario: Extract First N Characters**
```dax
Product Code = LEFT(Products[ProductName], 3)
```

**Scenario: Extract Last N Characters**
```dax
File Extension = RIGHT(Documents[FileName], 3)
```

**Scenario: Get Text Length**
```dax
Name Length = LEN(Customers[CustomerName])
```

**Scenario: Replace Text**
```dax
Formatted Phone = SUBSTITUTE(Customers[Phone], "-", "")
```

**Scenario: Trim Spaces**
```dax
Clean Name = TRIM(Customers[CustomerName])
```

---

#### Example 9: Logical Combinations

**Scenario: Check Multiple Conditions (AND)**
```dax
High Priority Flag = 
IF(
    AND(
        Orders[Amount] > 5000,
        Orders[Region] = "North"
    ),
    "Yes",
    "No"
)
```

**Scenario: Check Any Condition (OR)**
```dax
VIP Customer = 
IF(
    OR(
        Customers[TotalSpent] > 100000,
        Customers[MembershipLevel] = "Platinum"
    ),
    "VIP",
    "Regular"
)
```

**Scenario: Complex Logic**
```dax
Special Discount = 
IF(
    AND(
        OR(
            Sales[Quantity] >= 10,
            Sales[CustomerType] = "Wholesale"
        ),
        Sales[ProductCategory] = "Electronics"
    ),
    0.15,
    0.05
)
```

---

#### Example 10: Ranking and Grouping

**Scenario: Create Price Bands**
```dax
Price Band = 
SWITCH(
    TRUE(),
    Products[Price] < 50, "$0-$50",
    Products[Price] < 100, "$50-$100",
    Products[Price] < 500, "$100-$500",
    "$500+"
)
```

**Scenario: Revenue Buckets**
```dax
Revenue Bucket = 
SWITCH(
    TRUE(),
    Sales[Revenue] < 1000, "< $1K",
    Sales[Revenue] < 5000, "$1K-$5K",
    Sales[Revenue] < 10000, "$5K-$10K",
    ">= $10K"
)
```

---

### Best Practices for Calculated Columns

#### ✅ DO:

1. **Use for Row-Level Calculations**
```dax
// Good - Row-level calculation
Profit Per Item = Sales[Revenue] - Sales[Cost]
```

2. **Use for Categorization**
```dax
// Good - Creating categories
Customer Segment = IF(Customers[TotalSpent] > 10000, "Premium", "Standard")
```

3. **Use for Data Preparation**
```dax
// Good - Preparing data for analysis
Full Date = FORMAT(Sales[Date], "YYYY-MM-DD")
```

4. **Use Descriptive Names**
```dax
// Good
Order Total Amount Including Tax = Sales[Subtotal] * 1.08

// Not ideal
Col1 = Sales[Subtotal] * 1.08
```

#### ❌ DON'T:

1. **Don't Use for Aggregations** (Use Measures Instead)
```dax
// Bad - Creates column with same value in every row
Total All Sales = SUM(Sales[Amount])  // Use MEASURE instead!
```

2. **Don't Create Too Many Calculated Columns**
- Each column uses memory
- Slows down model performance
- Create only what you need

3. **Don't Use When a Measure Would Work Better**
```dax
// Bad - If you only need totals in visuals
Sales Total Column = SUM(Sales[Amount])  // Should be a MEASURE

// Good - Use measure instead
Sales Total Measure = SUM(Sales[Amount])
```

---

### Troubleshooting Calculated Columns

#### Error: "A single value for column cannot be determined"
```dax
// Problem: Using aggregate function without proper context
Bad Column = SUM(Sales[Amount])

// Solution: Remove aggregation or use SUMX
Good Column = Sales[Quantity] * Sales[Price]
```

#### Error: "Column doesn't exist"
```dax
// Problem: Wrong table or column name
Bad = Sales[Amound]  // Typo

// Solution: Check spelling, use IntelliSense
Good = Sales[Amount]
```

#### Error: "Calculation error in column"
```dax
// Problem: Division by zero
Bad = Sales[Profit] / Sales[Cost]

// Solution: Use DIVIDE with alternate result
Good = DIVIDE(Sales[Profit], Sales[Cost], 0)
```

---

## 4. Calculated Columns vs Measures

### The Most Important Distinction in DAX

Understanding the difference between calculated columns and measures is **CRITICAL** for:
- Writing efficient DAX
- Building performant models
- Creating the right calculations
- Managing memory usage

---

### Calculated Columns - Deep Dive

#### What Are They?

**Definition:**
Physical columns added to tables, calculated row-by-row using DAX formulas.

#### Visual Representation:
```
Orders Table:
OrderID | Quantity | Price | Total (Calculated Column) ← Stored in table
1       | 5        | 10    | 50
2       | 3        | 20    | 60
3       | 10       | 15    | 150
```

#### Characteristics:

**Storage:**
- ✅ Stored physically in the data model
- ⚠️ Takes up memory (can be compressed)
- 📊 Visible in Data View as a column

**Evaluation:**
- 🔄 Calculated when data refreshes
- 📝 Row context (one row at a time)
- ⏱️ Computed once and stored

**Usage:**
- 🎯 Can be used in filters, slicers, rows, columns
- 📊 Shows in table visuals
- 🔍 Can be used to create groups

**Performance:**
- ⚠️ Increases model size
- 🐌 Can slow down refresh times
- 💾 Uses more memory

#### When to Use Calculated Columns:

✅ **Use Cases:**

1. **Creating Categories/Groups**
```dax
Sales Category = 
IF(Sales[Amount] > 5000, "High", 
    IF(Sales[Amount] > 1000, "Medium", "Low"))
```

2. **Extracting Date Parts**
```dax
Year = YEAR(Orders[OrderDate])
Month = FORMAT(Orders[OrderDate], "MMMM")
Quarter = "Q" & QUARTER(Orders[OrderDate])
```

3. **Row-Level Calculations**
```dax
Profit = Sales[Revenue] - Sales[Cost]
Line Total = Sales[Quantity] * Sales[UnitPrice]
```

4. **Data Preparation**
```dax
Full Name = Customers[FirstName] & " " & Customers[LastName]
Full Address = Customers[Street] & ", " & Customers[City]
```

5. **Lookups from Related Tables**
```dax
Product Category = RELATED(Products[Category])
Customer Name = RELATED(Customers[Name])
```

6. **Creating Keys**
```dax
Composite Key = Orders[OrderID] & "-" & Orders[LineNumber]
```

---

### Measures - Deep Dive

#### What Are They?

**Definition:**
Dynamic calculations evaluated on-demand based on filter context in visuals.

#### Visual Representation:
```
Not stored in table - exists only in calculations:

Visual showing: Total Sales = 260
This is calculated dynamically from:
OrderID | Quantity | Price
1       | 5        | 10
2       | 3        | 20
3       | 10       | 15
```

#### Characteristics:

**Storage:**
- ✅ NOT stored physically (formula only)
- ✅ Minimal memory usage
- ❌ NOT visible in Data View

**Evaluation:**
- 🔄 Calculated when used in visuals
- 🎯 Filter context (aggregates based on filters)
- ⚡ Computed dynamically every time

**Usage:**
- 📊 Used only in VALUES area of visuals
- ❌ Cannot be used in rows/columns/filters
- 🎯 Responds to slicers and filters

**Performance:**
- ✅ Better performance (not stored)
- ⚡ Fast calculation engine
- 💾 Low memory footprint

#### When to Use Measures:

✅ **Use Cases:**

1. **Aggregations (Most Common)**
```dax
Total Sales = SUM(Sales[Amount])
Average Order Value = AVERAGE(Sales[Amount])
Total Quantity = SUM(Sales[Quantity])
```

2. **Counts**
```dax
Total Orders = COUNTROWS(Orders)
Unique Customers = DISTINCTCOUNT(Sales[CustomerID])
```

3. **Ratios and Percentages**
```dax
Profit Margin % = DIVIDE(SUM(Sales[Profit]), SUM(Sales[Revenue]), 0) * 100
Growth Rate = DIVIDE([Current Year Sales] - [Previous Year Sales], [Previous Year Sales], 0)
```

4. **Time Intelligence**
```dax
Sales YTD = TOTALYTD(SUM(Sales[Amount]), 'Calendar'[Date])
Sales Previous Year = CALCULATE(SUM(Sales
