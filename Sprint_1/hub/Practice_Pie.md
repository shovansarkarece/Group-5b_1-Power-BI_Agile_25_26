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
