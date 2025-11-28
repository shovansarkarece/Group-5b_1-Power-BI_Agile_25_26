# Power BI Step-by-Step Guide — Explanation of Each Component
---

# 1. Introduction to Power BI

*Power BI is a business analytics platform used to connect, transform, visualize and share data.*

*Key areas of the Power BI Desktop interface:*

* **Report View**
  *Purpose:* Build visuals and arrange them on pages (dashboards).
  *Step-by-step:*

  * 1. Click the **Report** icon (left vertical bar).
  * 2. Drag fields from the *Fields* pane to the canvas to create visuals (charts, tables, cards).
  * 3. Use the *Visualizations* pane to change chart type, formatting and interactions.
       *Why it matters:* This is where end users interact with insights; measures and visuals respond to slicers and filters.

* **Data View**
  *Purpose:* Inspect table data row-by-row; create calculated columns.
  *Step-by-step:*

  * 1. Click the **Data** icon (table icon in left bar).
  * 2. Select a table to see its rows and columns.
  * 3. Create a new calculated column: *Modeling → New Column* and enter DAX.
       *Why it matters:* Useful for validating transformations, quick row-level checks, and creating columns that are stored in the data model.

* **Model View**
  *Purpose:* Manage relationships between tables and tune the data model.
  *Step-by-step:*

  * 1. Click the **Model** icon (diagram icon).
  * 2. Drag one column onto another to create a relationship, or edit an existing relationship.
  * 3. Set cardinality (one-to-many) and cross-filter direction.
       *Why it matters:* Correct relationships ensure measures and visuals aggregate correctly across tables.

**Screenshot placeholder:**
<img width="1893" height="1002" alt="image" src="https://github.com/user-attachments/assets/a41b4c16-cce1-4da0-94f4-e96113081201" />

---

# 2. Importing CSV Data

*This process brings raw CSV files into Power BI and allows you to inspect & prepare them in Power Query.*

*Step-by-step:*

* 1. **Home → Get Data → Text/CSV**.
* 2. Choose your CSV file and click **Open**.
* 3. Power BI shows a preview. Inspect delimiter detection and sample rows.
* 4. Choose **Load** (quick import) or **Transform Data** (opens Power Query Editor).

  * *Use **Transform Data** when you need to clean or reshape (recommended).*
* 5. In Power Query Editor you can change column types, split columns, remove headers, trim text, and more.
* 6. After transforming, click **Home → Close & Apply** to load the cleaned table into the model.

*Common checks when importing CSV:*

* Ensure column headers are correct (Promote Headers if necessary).
* Confirm data types (text, number, date) to prevent later DAX errors.
* Remove accidental blank rows or footer notes.

**Screenshot placeholder:**
<img width="1344" height="691" alt="image" src="https://github.com/user-attachments/assets/b7395c4e-654e-49c1-979b-b8c2a8f7d78b" />
---

# 3. Adding a Custom Column

*Adding a custom column in Power Query uses M code to create new values row-by-row (before data loads into the model).*

*When to use:* Calculations that transform or combine columns during load (e.g., Line Total = Quantity × UnitPrice).

*Step-by-step (Power Query Editor):*

* 1. Open **Transform Data** to enter Power Query Editor.
* 2. Select the table in the left queries pane.
* 3. Go to **Add Column → Custom Column**.
* 4. In the dialog:

  * Enter the *New column name* (e.g., `Line Total`).
  * Enter an M expression in the *Custom column formula* box: `=[Quantity] * [UnitPrice]`.
  * Click **OK**.
* 5. Verify results and column type (change to Decimal Number if needed).
* 6. Close & Apply to persist changes to Power BI model.

*Notes & tips:*

* M expressions are case-sensitive for column names and use brackets: `[ColumnName]`.
* Use `Number.FromText()` or `Text.Trim()` if data types or stray characters cause errors.

**Screenshot placeholders:**
<img width="1358" height="669" alt="image" src="https://github.com/user-attachments/assets/852fd175-4b4c-46a6-87a9-b5c110e61a1f" />


<img width="1344" height="708" alt="image" src="https://github.com/user-attachments/assets/9f1b1e1f-8342-4caf-adf6-3c5ec3925eac" />
---

# 4. Conditional Column

*Conditional columns let you set values based on logic (if/then/else) during data preparation.*

*Use case from your screenshot:* Keep category values only when Category = "Clothing"; otherwise set null.

*Step-by-step:*

* 1. In Power Query Editor, select the query.
* 2. Click **Add Column → Conditional Column**.
* 3. Give the column a name (e.g., `ClothingOnly`).
* 4. Build the rule:

  * If *[Category]* equals `"Clothing"` then *[Category]* else `null`.
* 5. Click **OK** and check the new column values.
* 6. Close & Apply.

*Advanced note:* You can chain multiple conditions (else if) or add numeric comparisons (e.g., Amount > 100).

**Screenshot placeholder:**
<img width="1322" height="686" alt="image" src="https://github.com/user-attachments/assets/26ed0c30-9e35-4eb2-971f-2823729ede9a" />


---

# 5. Group By (Power Query)

*Group By aggregates rows by one or more keys — useful for summarizing totals per category.*

*Use case from your screenshot:* Group by *Category* and sum *Amount*.

*Step-by-step:*

* 1. In Power Query Editor, select the table.
* 2. Click **Home → Group By**.
* 3. In the dialog:

  * Group by: `Category`
  * New column name: `TotalAmount`
  * Operation: `Sum`
  * Column: `Amount`
* 4. Click **OK** and review the aggregated table (one row per Category).
* 5. If needed, expand additional aggregated columns or perform further transformations.
* 6. Close & Apply.

*Tip:* Use *Advanced* in Group By to create multiple aggregations at once (sum, count, average).

**Screenshot placeholders:**
<img width="1363" height="727" alt="image" src="https://github.com/user-attachments/assets/d6e9926a-7815-4c6c-bca9-dccff365637e" />

<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/f88d181d-1aa1-4c68-9586-e3eacc334b2f" />

---

# 6. Creating Relationships Between Datasets (Model View)

*Relationships connect tables so filters and measures work across them — for example Orders → Customers.*

*Step-by-step:*

* 1. Go to **Model View** (diagram icon).
* 2. Inspect tables and their key columns (e.g., `CustomerID`, `ProductID`).
* 3. Drag the key from one table (one side) onto the matching column in another table (many side).
* 4. In the relationship dialog confirm:

  * Cardinality (One to Many)
  * Cross filter direction (Single or Both) — prefer *Single* unless needed otherwise
  * Make relationship active
* 5. Click **OK**.
* 6. Test relationship by creating a visual: put a Customer field and a measure from Orders — values should aggregate correctly.

*Guidelines:*

* Primary/lookup tables are on the *one* side (e.g., Customers).
* Fact tables (transactions) are on the *many* side (e.g., Sales).
* Avoid circular relationships; use bridge tables if necessary.

**Screenshot placeholder:**
<img width="1360" height="733" alt="image" src="https://github.com/user-attachments/assets/40bf63bd-8336-4657-a0ed-6e0b564c6cc7" />


---

# 7. Creating a Dashboard (Report View)

*Turning prepared data into a dashboard — arranging visuals, slicers, and formatting.*

*Step-by-step:*

* 1. In **Report View**, create a new page or use an existing one.
* 2. From *Fields* pane drag fields into the canvas — Power BI auto-selects a visualization type.
* 3. Change the visual type using the *Visualizations* pane (e.g., Bar chart, Line chart, Card, Pie).
* 4. Add **Slicers** (Insert → Slicer or drag a field to canvas and change to Slicer) to allow interactive filtering (e.g., Year, Region, Category).
* 5. Use **Format** options to style visuals: titles, axis labels, data colors, and labels.
* 6. Enable **Interactivity**: select a visual → Format → Edit interactions to control cross-filter behavior.
* 7. Add **Text boxes / Images** for titles and branding.
* 8. Test: click slicer options and visuals should update accordingly.
* 9. Save the PBIX file; publish to Power BI Service if you want web access / sharing.

*Best practices:*

* Place KPI cards at top for quick glance metrics.
* Keep visual count per page moderate (4–6) to avoid clutter.
* Use consistent color palette & labels.

**Screenshot placeholders:**
<img width="1361" height="708" alt="image" src="https://github.com/user-attachments/assets/9a1ab2e5-4402-41e8-8fef-025f6073f217" />

<img width="1340" height="683" alt="image" src="https://github.com/user-attachments/assets/b2527b07-27d7-4e14-9ced-9d477c8c9858" />

---

# 8. Practice Project — Full Flow Summary

*Steps to reproduce the workflow in your screenshots:*

* 1. **Get Data** → Import CSV into Power BI.
* 2. **Transform Data** → Power Query: clean types, trim text, promote headers.
* 3. **Add Column** → Custom Column `Line Total = [Quantity] * [UnitPrice]`.
* 4. **Conditional Column** → `ClothingOnly = if [Category] = "Clothing" then [Category] else null`.
* 5. **Group By** → `Category` → Sum `Amount` to get `TotalAmount`.
* 6. **Close & Apply** to load queries into model.
* 7. **Model View** → Create relationships (e.g., Sales → Products on `ProductID`).
* 8. **Report View** → Build dashboard with slicers, cards, charts and a table showing grouped totals.
* 9. **Test & Save** → Interact with slicers; verify calculations update correctly.

---

# 9. Useful Tips & Troubleshooting

*Data & Types*

* Always check column data types in Power Query — dates and numbers must be typed correctly.
* If a numeric column imports as text, use *Transform → Data Type → Decimal Number* or `Number.FromText()` in Custom Column.

*Broken visuals / wrong aggregations*

* If a visual returns unexpected totals, check relationships and cardinality.
* Use *SUMX* or iterators when row-by-row calculation is needed in DAX.

*Performance*

* Avoid unnecessary calculated columns if a measure can do the job (measures are evaluated on demand and use less memory).
* Remove unused columns before loading to reduce model size.

*Common errors*

* #VALUE or errors in custom column: inspect sample rows for non-numeric text or nulls. Use `try ... otherwise` in M for safe conversions.
* Slicer not filtering visual: check relationships and cross-filter direction.

---

# End — Quick Reference Commands

*Power Query*

* Add Column → Custom Column → `=[Quantity] * [UnitPrice]`
* Add Column → Conditional Column → configure if/then rules
* Home → Group By → aggregate (Sum, Count, Avg)

*Report View*

* Modeling → New Measure → `Total Sales = SUM(Sales[Line Total])`
* Insert → Slicer → drag field (e.g., Year)
* Visualizations → Format → Edit interactions

---
