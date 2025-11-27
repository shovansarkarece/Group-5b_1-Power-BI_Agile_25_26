# Power BI DAX - Practical Step-by-Step Guide

---

# Table of Contents
* 1. DAX Syntax Basics  
* 2. Common DAX Functions (quick)  
* 3. Creating Calculated Columns — Step by Step  
* 4. Creating Measures — Step by Step  
* 5. Calculated Columns vs Measures (short)  
* 6. Practice Exercises (compact)  
* 7. Quick Reference & Troubleshooting

---
# 1. DAX Syntax Basics

* **What is DAX?**  
  DAX (Data Analysis Expressions) is the formula and calculation language used in Power BI, Power     Pivot, and Analysis Services. It allows you to create custom    calculations such as totals, averages, percentages, KPIs, time intelligence metrics, and row-level logic.

  DAX works on top of your data model and enables Power BI to perform dynamic, context-aware calculations that respond to filters, slicers, and relationships.

* **Basic rules**
  * Always start with `=`.  
  * Use `Table[Column]` (use `'Table Name'[Column]` if spaces).  
  * Functions are written in UPPERCASE (SUM, AVERAGE).  
  * Use `&` to concatenate text.  
  * Comments: `//`.

* **Example**  
  `Total Sales = SUM(Sales[Amount])`

---

# 2. Common DAX Functions (quick)

* **Aggregation**
  * `SUM(Table[Column])` — totals  
  * `AVERAGE(Table[Column])` — mean  
  * `COUNTROWS(Table)` — count records (preferred)

* **Text / Date**
  * `UPPER(text)`, `LOWER(text)`, `FORMAT(date, "MMMM")`
  * `YEAR(Date)`, `QUARTER(Date)`, `DATEDIFF(start, end, YEAR)`

* **Logical / Safety**
  * `IF(condition, true, false)`  
  * `DIVIDE(n, d, 0)` — avoids division-by-zero

---

# 3. Creating Calculated Columns — Step by Step

*When to use:* row-level values (stored), categories, lookups via relationships.

**Step 1 — Load & go to Data View**  
* Home → Get Data → load → Close & Apply → Click **Data** icon.

**Step 2 — New Column**  
* Modeling → New Column → formula bar appears.

**Step 3 — Write formula & Enter**  
* `ColumnName = <expression>` → Enter → column stored in table.

**Examples**
* Line Total (row math):  
  `Line Total = Sales[Quantity] * Sales[UnitPrice]`
* Extract Year:  
  `Order Year = YEAR(Orders[OrderDate])`
* Category with nested IFs:  
```
Sales Category =
IF(Sales[Amount] > 5000, "High",
IF(Sales[Amount] > 1000, "Medium", "Low"))






