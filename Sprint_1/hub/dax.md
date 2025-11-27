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
