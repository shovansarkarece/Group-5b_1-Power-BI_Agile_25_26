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
