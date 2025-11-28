# How to create a Pie Chart in Power BI — Step-by-Step

---

# Create a Pie Chart — Quick Overview

A Pie Chart shows parts of a whole. You need:

* **Category** field (slices) — e.g., Product Category, Region
* **Value** field (slice size) — numeric measure or column (sales, quantity)

---

# Steps — Prepare the data (quick checks)

* Open your Power BI **.pbix** and go to **Report View**.
* Make sure the table/columns you want are loaded and have correct data types:

  * Category = Text
  * Value = Number (decimal/whole)

If your value is not numeric, convert it in **Power Query** or create a measure:

```
Total Sales = SUM(Sales[Amount])
```

---

# Steps — Build the Pie Chart

1. **Go to Report View** (bar chart icon on left).
2. **Insert a Pie visual**:

   * From the *Visualizations* pane click the *Pie chart* icon. A blank pie visual appears on the canvas.
3. **Add the Category**:

   * Drag the category field (e.g., `Products[Category]`) into the *Legend* or *Details* area of the visual.
4. **Add the Value**:

   * Drag the numeric field or measure (e.g., `Total Sales`) into the *Values* area. Power BI will auto-aggregate (SUM by default).
5. **Resize & place** the visual on the page as needed.

---

# Steps — Show percentages and values

1. Select the pie visual.
2. Open the **Format** pane (paint roller icon).
3. Expand **Data labels**:

   * Turn **Data label** = *On*.
   * For **Label style** pick *Data value*, *Category, data value* or *Percentage* depending on what you want to display.
   * Use **Display units** and **Decimal places** to control formatting.
4. Optionally show both value and percent by creating a measure:

```
Percent of Total = 
DIVIDE(
    SUM(Sales[Amount]),
    CALCULATE(SUM(Sales[Amount]), ALL(Sales)),
    0
)
```

Then add that measure to Tooltip or use it as needed.

---

# Steps — Make it a Donut (if desired)

1. With the pie selected, go to **Format → Shapes**.
2. Increase **Inner radius** (e.g., 40–60) to create a donut look.

---

# Steps — Sort slices and control slice order

* By default Power BI sorts slices by legend or by the value.
* To change it: click the **ellipsis (...)** in the visual → **Sort by** → choose field (e.g., `Total Sales`) and **Sort descending/ascending**.

---

# Steps — Group small slices into “Other”

**Option A — Use Visual-level filter (Top N)**

1. With visual selected → Filters pane → drag the category field to the visual filter.
2. Choose **Top N**, set N (e.g., Top 5 by `Total Sales`), click **Apply filter**. This shows top N slices and groups the rest under *Other* automatically (Power BI shows only top N unless you enable “Show all other values”).

**Option B — Create a grouped column in the Fields pane**

1. Right-click the category field → **New group**.
2. Use *Bins/Manual grouping* to combine smaller categories into one group called *Other*.
3. Use this grouped field in the pie.

**Option C — DAX grouping** (advanced)

```dax
Category Group = 
VAR RankCategory = RANKX(ALL('Products'[Category]), [Total Sales], , DESC)
RETURN IF(RankCategory <= 5, 'Products'[Category], "Other")
```

Then use `Category Group` as the Legend.

---

# Steps — Format legend, labels & tooltips

* **Legend**: Format → Legend → Position (Right, Top, Bottom), Text size, Title.
* **Data labels**: Format → Data labels → Color, text size, display units.
* **Tooltip**: Drag additional fields or measures into the visual’s Tooltip well to show richer info when hovering.
* **Detail labels**: Format → Detail labels (if available) for leader lines or label density control.

---

# Steps — Interactivity & Drillthrough

* **Cross-filtering**: By default clicking a pie slice cross-filters other visuals. Edit interactions: select a visual → Format → Edit interactions.
* **Drilldown**: If your Legend uses a hierarchical field (Category → Subcategory), add both fields into the Legend/Details to enable drill-down arrows on the visual.

---

# Steps — Accessibility & best practices

* Avoid >8–10 slices — pie charts become hard to read. Consider bar charts for many categories.
* Use contrasting colors for adjacent slices. Format → Data colors → assign colors.
* Add a title and concise subtitle. Format → Title.
* Provide exact numbers in tooltips or a small adjacent table for precise comparison.
* For dashboards, keep the pie size readable on target screens (desktop/tablet/mobile).

---

# Troubleshooting common issues

* **Slices look too small or tiny** → group small categories into *Other* or switch to a bar chart.
* **Percentages don’t add to 100%** → check for filters or missing/null values; include `SHOW AS % OF GRAND TOTAL` measure instead.
* **Blank slice shown** → filter out blank/null categories or replace null with "Unknown".

  * In Power Query: replace nulls in Category with "Unknown" or in visual filter remove blanks.

---

# Example checklist before publishing

* Data types are correct (Category = text, Value = number).
* Labels show either % or value (or both via tooltip).
* Legend fits and is readable.
* Small categories are grouped if needed.
* Interactions tested (click slice → other visuals update).
* Saved and (if applicable) pinned to dashboard.

  # How to create a Map in Power BI — Step-by-Step

---

# 1. Quick overview — which map to use

* **Map (Bubble map)** — plots points by latitude/longitude or place name; bubble size = value.
* **Filled Map (Choropleth)** — fills geographic areas (countries, states, postal codes) with color by value.
* **Shape map** — custom TopoJSON shapes for advanced choropleths (requires shape file).
* **ArcGIS Maps for Power BI** — richer mapping (layers, clustering, spatial analysis).
* **Azure Maps / Mapbox (custom visual)** — advanced styling / base maps (may require keys).

---

# 2. Prepare your data

* *Minimum needs for point maps*: a geographic field (City, Country, PostalCode, Address) **or** numeric *Latitude* and *Longitude*.
* *For filled maps*: a region identifier Power BI recognizes (Country, State, County, Region).
* *Clean data*: remove typos, standardize country/state names.
* *Data types*: ensure numeric fields (lat/lon, measure) are numbers; geographic fields are text.
* *Add columns if needed*: split full address into parts or geocode lat/lon outside Power BI.

**Tip:** If names are ambiguous, prefer **Latitude / Longitude** for exact placement.

---

# 3. Set data category for geography columns

1. In **Data View**, select the table column (e.g., `Country`, `City`, `PostalCode`, `Latitude`, `Longitude`).
2. Go to **Column tools → Data category** and choose the correct category:

   * *Country/Region*, *State or Province*, *City*, *Postal Code*, *Address*, *Latitude*, *Longitude*.
3. This helps Power BI (Bing/Map engines) resolve locations more accurately.

---

# 4. Create a basic Bubble Map

1. **Report View** → click the **Map** visual icon in the Visualizations pane.
2. Drag **Location** field into *Location* (e.g., `City`, `Address`, or use `Latitude` + `Longitude` instead).

   * If using lat/lon, put `Latitude` in *Latitude* well and `Longitude` in *Longitude* well.
3. Drag a numeric field (e.g., `Sales`) into *Size* (controls bubble size).
4. (Optional) Drag a field into *Legend* to color bubbles by category (e.g., `Region`).
5. Resize and position the visual on the report canvas.

**Format:**

* Format → **Data colors** to choose palette.
* Format → **Bubbles** to adjust maximum bubble size & outline.
* Format → **Map controls** → enable/disable zoom, pan, labels.

---

# 5. Create a Filled Map (Choropleth)

1. Insert the **Filled map** visual from Visualizations.
2. Drag a geographic field recognized as a region (e.g., `Country`, `State`) into *Location*.
3. Drag a numeric measure (e.g., `Total Sales`) into *Color saturation* (the value that colors areas).
4. Use format → **Data colors** to set color gradient and **Diverging** if you want a midpoint.
5. If some regions are missing, fix by ensuring names match Power BI’s recognized list (or use ISO codes).

**Note:** Filled maps rely on Bing maps; for small subregions (custom regions) use Shape map.

---

# 6. Using Latitude & Longitude

1. In the visual’s fields: put `Latitude` into *Latitude* well and `Longitude` into *Longitude* well.
2. If your lat/lon are stored as text, convert to decimal numbers in Power Query or set data type to Decimal Number.
3. Confirm **Data category** is set to *Latitude* and *Longitude*.

---

# 7. Shape Map (custom TopoJSON)

*For custom shapes (sales territories, custom regions).*

1. Enable Shape Map preview (if required): **File → Options and settings → Options → Preview features → Shape map visual**. Restart Power BI if toggled.
2. Prepare a TopoJSON file with your custom regions (GeoJSON converted to TopoJSON).
3. Insert **Shape map** visual.
4. Format → **Shape** → **+ Add Map** → upload TopoJSON.
5. Drag the region key (must match the TopoJSON feature IDs/names) to *Location* and a measure to *Color saturation*.
6. Format color scale and legend.

**Tip:** Keep TopoJSON file size small; complex shapes hurt performance.

---

# 8. ArcGIS Maps and other advanced visuals

*ArcGIS gives clustering, heat maps, reference layers, and demographic data.*

1. From the Visualizations pane, select **ArcGIS Maps for Power BI** (available by default).
2. Sign in if requested (free tier available).
3. Add Location and Size similar to Map.
4. Use ArcGIS layer options to add reference layers, heat maps, clustering, drive-time areas.

**Note:** ArcGIS may require an ArcGIS account for full features.

---

# 9. Tooltips & Interactivity

*Tooltips:*

* Drag additional fields into the visual’s **Tooltips** well to show more info on hover (e.g., `StoreName`, `Sales`, `Margin`).
* Create **report page tooltips** for rich custom tooltip pages.

*Interactivity:*

* Clicking a map bubble slice will cross-filter other visuals by default.
* Edit interactions: select visual → Format → Edit interactions.

---

# 10. DAX examples for map values

*Example measure for bubble size (Total Sales):*

```dax
Total Sales = SUM(Sales[Amount])
```

*Percent of total (for tooltip):*

```dax
Percent of Total = DIVIDE([Total Sales], CALCULATE([Total Sales], ALL(Sales)), 0)
```

*Top N group for map legend (show Top 10 cities, rest = Other):*

```dax
City Group = 
VAR RankCity = RANKX(ALL(Sales[City]), [Total Sales], , DESC)
RETURN IF(RankCity <= 10, Sales[City], "Other")
```

---

# 11. Formatting & UX best practices

* Keep legend and labels readable (avoid overlapping labels).
* Use consistent color scales; use **Diverging** for positive/negative values.
* Use **Tooltips** to show exact numbers; avoid cluttering the map with labels.
* For many points, use clustering or reduce detail (top N) to improve readability.
* If showing global data, test projections and colorblind-friendly palettes.

---

# 12. Performance tips

* Limit the number of plotted points — use aggregation (Group By) when possible.
* Use **DirectQuery** carefully — maps with many tiles and queries can be slow.
* Avoid extremely detailed TopoJSON shapes on Shape map.
* Use server-side geocoding (pre-calculate lat/lon) rather than relying on Bing for many records.

---

# 13. Troubleshooting common issues

* **Points not appearing / wrong location:**

  * Check `Latitude`/`Longitude` numeric types and that Data Category is set correctly.
  * If using place names, ensure spelling matches recognized names (try Country/State iso codes).
* **Many locations incorrectly resolved to a single place:**

  * Ambiguous city names require country context. Put `City` in **Location** and `Country` in **Tooltips** or combine into `City, Country`.
* **Blank areas in Filled Map:**

  * Names mismatch — use ISO codes or clean names.
* **Map shows network error or Bing blocked:**

  * Corporate networks sometimes block Bing maps — try from home or check network policy.
* **Shape map displays empty / mismatched regions:**

  * Ensure TopoJSON feature `id` or `name` matches your data keys exactly.
  * 
---

# 15. Example workflow 

* Power Query: clean geography fields → set data types → add Latitude/Longitude if you have them.
* Data View: set Data Category for geo columns.
* Report View: insert Map / Filled Map / Shape map → drag Location + Size → format labels and colors → test interactions → save.

---

# Power BI — Detailed Step-by-Step Guide: How to Clean Data

---

# 1. Overview — When & Why to Clean Data

* Cleaning in **Power Query Editor** ensures reliable analysis, correct aggregations, and smaller/faster data models.
* Do cleaning **before** loading data into the model (Transform Data → Power Query Editor).
* Keep steps small, named, and documented in the **APPLIED STEPS** pane.

---

# 2. Open Power Query Editor

* Home → **Transform data** (Power BI Desktop).
* Left pane shows queries (tables) — pick the query to clean.
* Use the **Preview** window to inspect rows and columns.

---

# 3. First checks (quick audit)

* *Column headers* — Are they correct, or do you need to **Promote headers**?

  * Home → Use First Row as Headers (if required).
* *Column types* — Numbers/dates/text must be set correctly.

  * Transform → Data Type → choose appropriate type.
* *Column quality & distribution* — View **Column quality**, **Column distribution**, **Column profile** (View → Column quality / distribution / profile). These reveal nulls, error rates, and value spread.

---

# 4. Common cleaning tasks — step-by-step

## 4.1 Trim and Clean text

*Why:* Remove leading/trailing spaces and non-printable characters that break joins or filters.

**UI steps:**

1. Select text column(s).
2. Transform → Format → **Trim**.
3. Transform → Format → **Clean** (removes non-printable chars).

**M example:**

```m
= Table.TransformColumns(PreviousStep, {{"Name", Text.Trim, type text}})
```

---

## 4.2 Change / enforce data types

*Why:* Calculations and visuals rely on correct types (dates for time intelligence; numbers for sums).

**UI steps:**

1. Select column → Transform → Data Type → choose (Decimal Number, Whole Number, Date, Date/Time, Text, etc.).
2. Or use column header type icon → choose type.

**M example:**

```m
= Table.TransformColumnTypes(PreviousStep, {{"OrderDate", type date}, {"Amount", type number}})
```

---

## 4.3 Remove top/bottom/alternate/blank rows

*Why:* Remove file footers, extra header rows, or blank rows.

**UI steps:**

* Home → Reduce Rows → Remove Rows → **Remove Top Rows** / **Remove Bottom Rows** / **Remove Blank Rows** / **Remove Alternate Rows**.

**M examples:**

```m
= Table.Skip(Source,4)  // remove top 4 rows
= Table.SelectRows(Source, each not List.IsEmpty(Record.FieldValues(_))) // remove fully blank rows
```

---

## 4.4 Promote headers / use first row as header

*Why:* Ensure column names are the actual headers.

**UI steps:**

* Home → Use First Row as Headers.

**M:**

```m
= Table.PromoteHeaders(PreviousStep, [PromoteAllScalars=true])
```

---

## 4.5 Remove duplicates

*Why:* Prevent double-counting.

**UI steps:**

* Select column(s) → Home → Remove Rows → **Remove Duplicates**.

**M:**

```m
= Table.Distinct(PreviousStep, {"OrderID"})
```

---

## 4.6 Replace Values / Replace Errors

*Why:* Standardize placeholders (e.g., "N/A", "-", "unknown") and handle errors.

**UI steps:**

* Home → Replace Values → enter *Value To Find* and *Replace With*.
* Transform → Replace Errors → specify replacement.

**M:**

```m
= Table.ReplaceValue(PreviousStep,"N/A",null,Replacer.ReplaceValue,{"Status"})
= Table.ReplaceErrorValues(PreviousStep, {{"Amount", 0}})
```

---

## 4.7 Split & Merge columns

*Why:* Separate combined fields or combine address parts.

**Split UI steps:**

* Select column → Transform → Split Column → By Delimiter / By Number of Characters / By Positions.

**Merge UI steps:**

* Select multiple columns (Ctrl+click) → Transform → Merge Columns → choose delimiter.

**M (split by delimiter):**

```m
= Table.SplitColumn(PreviousStep, "FullName", Splitter.SplitTextByDelimiter(" ", QuoteStyle.Csv), {"FirstName","LastName"})
```

**M (merge):**

```m
= Table.CombineColumns(PreviousStep,{"FirstName","LastName"},Combiner.CombineTextByDelimiter(" "), "FullName")
```

---

## 4.8 Fill Down / Fill Up

*Why:* Propagate values in hierarchical datasets where categories appear only once per block.

**UI steps:**

* Select column → Transform → Fill → Down (or Up).

**M:**

```m
= Table.FillDown(PreviousStep,{"Region"})
```

---

## 4.9 Filter rows (remove outliers, keep ranges)

*Why:* Remove irrelevant data or limit by date range.

**UI steps:**

* Click filter icon on column → uncheck unwanted values or use Text/Number/Date filters (e.g., Date After, Greater Than).

**M:**

```m
= Table.SelectRows(PreviousStep, each [Amount] > 0 and [OrderDate] >= #date(2023,1,1))
```

---

## 4.10 Conditional Column (if/then logic)

*Why:* Classify or flag records during import.

**UI steps:**

* Add Column → Conditional Column → set conditions.

**M (Custom Column alternative):**

```m
= Table.AddColumn(PreviousStep, "SalesCategory", each if [Amount] > 5000 then "High" else if [Amount] > 1000 then "Medium" else "Low")
```

---

## 4.11 Pivot / Unpivot

*Why:* Convert between wide and long formats for analysis.

**Pivot UI:**

* Select column to pivot → Transform → Pivot Column → select values and aggregation.

**Unpivot UI:**

* Select columns to keep → Transform → Unpivot Other Columns (or Unpivot Columns).

**M (unpivot example):**

```m
= Table.UnpivotOtherColumns(PreviousStep, {"ProductID"}, "Attribute", "Value")
```

---

## 4.12 Group By / Aggregations

*Why:* Summarize data (totals, counts, averages) before loading.

**UI steps:**

* Home → Group By → choose group column(s), operation (Sum, Count, Average) and column to aggregate.

**M:**

```m
= Table.Group(PreviousStep, {"Category"}, {{"TotalAmount", each List.Sum([Amount]), type number}, {"Count", each Table.RowCount(_), Int64.Type}})
```

---

## 4.13 Merge Queries (joins)

*Why:* Combine related tables (lookup, enrichment).

**UI steps:**

* Home → Merge Queries (or Merge Queries as New) → select primary and secondary tables → click matching columns → choose join type (Left, Inner, Right, Full, Anti).
* Expand the nested table column to select fields to bring in.

**M:**

```m
= Table.NestedJoin(Orders, {"CustomerID"}, Customers, {"CustomerID"}, "Customers", JoinKind.LeftOuter)
= Table.ExpandTableColumn(PreviousStep, "Customers", {"CustomerName","Country"}, {"CustomerName","Country"})
```

---

## 4.14 Append Queries (stacking sheets/tables)

*Why:* Combine multiple sheets/monthly files of same schema into one table.

**UI steps:**

* Home → Append Queries → Append Queries as New → choose two or three+ tables.

**M:**

```m
= Table.Combine({Jan, Feb, Mar})
```

---

## 4.15 Detect data types & use Column Profiling

*Why:* Identify errors, nulls, value distribution.

**UI steps:**

* View → enable **Column quality**, **Column distribution**, **Column profile**.
* Address issues flagged: convert types, replace errors, trim, remove blanks.

---

# 5. Advanced & Safety steps

## 5.1 Use Parameters & Templates

*Why:* Reuse queries across files (folder sources for monthly loads). Create parameterized file paths.

**UI:** Home → Manage Parameters → create parameter → use in File path for Source step.

## 5.2 Use Folder connector & Combine Files

*Why:* Automate appending new files placed in a folder.

**UI:** Home → Get Data → Folder → Combine & Transform Data → Power Query auto-generates a function and a combined table.

## 5.3 Use `try ... otherwise` to prevent step failures

**M example:**

```m
= Table.AddColumn(PreviousStep, "SafeAmount", each try Number.FromText([Amount]) otherwise 0)
```

## 5.4 Use `Table.Buffer()` sparingly for performance

*Why:* Buffer when reusing a table many times in the same query to reduce recomputation — but can increase memory usage.

**M example:**

```m
let
  src = Table.Buffer(Source),
  // further steps using src
in
  final
```

---

# 6. Naming & documenting applied steps

* Rename steps in **APPLIED STEPS** to meaningful names (e.g., `PromoteHeaders`, `TrimNames`, `ChangeType_OrderDate`).
* Keep steps small and atomic (1 transformation per step) — easier to debug and edit.

---

# 7. Validate & test

* Spot-check rows and edge cases after each major transform.
* Use **Remove Other Columns** on a sample query to focus on problem columns.
* Use **Keep Top Rows** to test on small samples quickly.
* Check totals before/after transforms to ensure values preserved (e.g., total sales).

---

# 8. Load Strategy & final steps

* After cleaning, **Home → Close & Apply** to load to the model.
* Consider removing unused columns before load to reduce model size.
* Where possible create **measures** (DAX) instead of heavy calculated columns to save memory.

---

# 9. Common pitfalls & troubleshooting

* **Wrong totals after joins** — check relationship cardinality and duplicated keys from merge.
* **Dates not aggregating** — confirm type = Date and consistent formatting.
* **Unexpected nulls** — check Trim/Clean and Replace Values steps; watch for hidden characters.
* **Step fails after file change** — use robust parsing (e.g., promote headers conditionally) or parameters.

---

# 10. Useful M snippets (copy/paste)

*Remove rows with null in a column*

```m
= Table.SelectRows(PreviousStep, each Record.FieldValues(_){0} <> null)
```

*Convert currency string to number (remove € and commas)*

```m
= Table.TransformColumns(PreviousStep, {{"Price", each Number.FromText(Text.Replace(Text.Replace(_, "€", ""), ".", "")), type number}})
```

*Safe parse date*

```m
= Table.AddColumn(PreviousStep, "SafeDate", each try Date.FromText([DateText]) otherwise null, type date)
```

*Group by Category and count*

```m
= Table.Group(PreviousStep, {"Category"}, {{"Count", each Table.RowCount(_), Int64.Type}})
```

---

# 11. Performance tips

* Remove columns you don’t need before complex steps.
* Reduce cardinality of columns where possible (avoid high-cardinality text used as keys).
* Prefer native query folding (keep transformations that push to source, e.g., filters, column selection — check step folding icon).
* Use incremental refresh (Power BI Pro/Premium) for large datasets.

---

# 12. Checklist before sharing your PBIX

* All data types correct.
* No unexpected errors in queries.
* Applied steps named and logical.
* Remove PII (if needed).
* Save PBIX and document key transformations (README or .md notes).

---

# 13. Example mini workflow 

1. Get Data → CSV/Excel/Folder → Transform Data.
2. Promote headers → Trim/Clean text → Change data types.
3. Replace values / remove blank rows / remove duplicates.
4. Split/merge columns as necessary.
5. Add calculated columns (M) or conditional columns.
6. Group By / Aggregate if needed.
7. Merge with lookup tables or Append multiple sources.
8. Final validation → Close & Apply.

---

