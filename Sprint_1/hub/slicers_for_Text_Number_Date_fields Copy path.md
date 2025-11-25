## ✅ Task Overview
1. Add slicers for Text, Number, and Date fields


<img width="1917" height="1021" alt="Screenshot 2025-11-25 230441" src="https://github.com/user-attachments/assets/b58e6dcc-b641-493c-b35c-dc9bd7da9593" />


📘 Creating a Text Slicer in Power BI

A text slicer in Power BI allows users to filter visuals based on text fields such as Category, Region, Product Name, or any other string-based column.
In this example, the slicer filters data by Category (Furniture, Office Supplies, Technology).

🧩 What is a Text Slicer?

A text slicer is a filtering visual that displays a list of text values.
Users can click one or more text options to dynamically filter other visuals on the report page.

In the screenshot, a horizontal text slicer is displayed with three selectable buttons:

Furniture

Office Supplies (selected state)

Technology

📌 How to Create a Text Slicer in Power BI

Follow the steps below to create the same text slicer in your Power BI report.

1️⃣ Load Your Dataset

Open Power BI Desktop.

Go to Home → Get Data.

Import your dataset (Excel, CSV, SQL, etc.).

Ensure your table contains a text column (e.g., Category).

2️⃣ Add a Slicer Visual

On the Visualizations pane (right side), click the Slicer icon


A blank slicer appears on the report canvas.

3️⃣ Add a Text Field to the Slicer

In the Fields pane, expand your table (e.g., Orders).

Drag the Category field into the slicer’s Field box.

The slicer now displays a vertical list of text values.

4️⃣ Change the Slicer Orientation to Horizontal (Optional)

To replicate your screenshot layout:

Select the slicer visual.

In the Visualizations → Format pane, find Slicer settings.

Change Orientation from Vertical to Horizontal.

The slicer now displays text options as buttons aligned side-by-side.

5️⃣ Customize the Button Style

To achieve the modern look:

Button Style

Go to Format → Style.

Choose "Tile" or "Horizontal buttons" depending on your version.

Border & Background

Set Background to white for inactive items.

Set Background to dark (or theme color) for selected items.

Add a border and increase border thickness for better visibility.

Text Formatting

Increase Font size for readability.

Use centered alignment.

6️⃣ Enable Selection Options (Single/Multiple)

Depending on your use-case:

Single Select
Only one text item can be selected
(Good for category-switching dashboards)

Multi-Select
Users can choose multiple text values
(Useful for comparing more than one segment)

To change selection behavior:

Go to Format → Selection controls.

Enable/disable:

Single select

Multi-select with CTRL

Select all option

7️⃣ Link the Slicer to Other Visuals

Power BI automatically filters all visuals on the same page.

If needed, customize interactions:

Select the slicer.

Go to Format → Edit interactions.

Choose how each visual responds (Filter / Highlight / None).

---

📊 Power BI – Numeric Slicer for Profit

<img width="1919" height="1069" alt="2" src="https://github.com/user-attachments/assets/fa8a5442-9e69-41f8-aa3d-1d528b3cb7c7" />


This page in Power BI Desktop demonstrates how to use a numeric slicer to filter data based on a measure called Profit, alongside a table showing Sales and Product Name.

🖥️ Layout Overview

The Power BI window is divided into several key areas:

Top Ribbon – Contains tabs like Home, Insert, Modeling, View, Optimize, Help, with actions such as:

Get data, Transform data, New visual, Text box, Publish, etc.

Report Canvas (Center) – Where the visuals are placed.

Right Side Panels:

Filters – “Filters on this page” and “Filters on all pages”.

Visualizations – Shows all chart types and formatting options.

Data – Lists fields from the Orders table (Category, City, Profit, Sales, Ship Date, etc.).

Bottom Navigation – Shows multiple pages: Page 1, Page 2, Page 3 (selected) and a + icon to add more pages.

📌 Visuals on This Page

There are two main visuals on the canvas:

1. Table Visual (Left Side)

A table is placed on the left side displaying:

Sales

Product Name

Each row represents a product with its corresponding sales value (displayed with decimals, e.g., 0.44, 0.56, 0.84, 0.99, 1.04, etc.).
Users can scroll to see more rows. The table is useful to observe how values change when the Profit slicer is adjusted.

2. Numeric Slicer for Profit (Right Side)

On the right side, there is a numeric slicer that filters the data based on Profit.

The slicer is titled “Profit”.

It uses a slider with two circular handles.

Above the slider, there are two numeric input boxes showing the minimum and maximum selected values (e.g., from -6.599,98 to 145,36 – formatted using local numeric settings).

Moving either handle will change the Profit range and filter the data on this page.

This slicer allows users to focus on products within a specific profit interval, such as:

Only highly profitable products,

Only low or negative profit products,

Or any custom range.

🛠️ How the Numeric Slicer Was Created

Below is a conceptual summary of how this Profit slicer is built (for documentation purposes):

Add a Slicer Visual

From the Visualizations pane, click the Slicer icon.

Assign the Profit Field

In the Data pane, drag the Profit field (from the Orders table) to the Field area of the slicer.

Set Numeric Mode

Power BI detects that Profit is numeric and automatically displays it as:

A between range with slider, or

You can change type (e.g., “Between”, “Less than”, “Greater than”) from the slicer header.

Format the Slicer (Optional)

Adjust number formatting (decimal places, thousand separator) using the Modeling → Format options.

In the Format pane, you can:

Show/hide the header.

Change the size of the slider.

Adjust the font and colors.

When the user moves the slider, all visuals on this page (including the Sales & Product Name table) are automatically filtered to show only rows within the chosen Profit range.

