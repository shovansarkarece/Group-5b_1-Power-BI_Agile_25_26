


## ✅ Task Overview
1. Load data from the Excel sheet
2. Create a Ribbon Chart based on **Category**
3. Create a Line Chart based on **Category**
4. Create an Area Chart based on **Category**

---

## 📌 Step 1: Load Data From Excel Sheet
1. Open **Power BI Desktop**.
2. Sign in using your account.
3. Click **Home → Get Data → Excel**.
4. Select your uploaded Excel file.
5. Choose the correct sheet (e.g., *Orders*).
6. Click **Load**.
<img width="1919" height="1005" alt="one" src="https://github.com/user-attachments/assets/86b9c489-c831-47ea-9e3c-d3de09bb9cbc" />

---
---

## Main Power BI Window (Background)

- The top area contains the **Ribbon** with tabs: Home, Insert, Modeling, View, Optimize, Help.
- You are currently on the **Home** tab, showing options such as:
  - **Get data**, **Excel workbook**, **SQL Server**, **Recent sources**
  - **Transform data**, **Refresh**
- The large white area behind the dialog is the **Report Canvas (Page 1)**, where visuals will be placed.
- On the right side:
  - **Visualizations Pane** – icons representing different chart types.
  - **Data/Fields Pane** – will show tables and fields after loading data.

---

## Navigator Window (Center)

The Navigator window appears after selecting an Excel file. It allows you to choose which sheets/tables to import.

### **Left Side – Table/Sheet List**

- Shows all available items in the Excel file:  
  - **Orders**  
  - **People**  
  - **Returns**
- The file `orders.xlsx` contains **3 items**.
- A checkbox next to each item allows selecting which tables to load.
- A **Search Box** is available to quickly find tables.
- **Display Options** lets you filter or rearrange how tables are shown.

### **Right Side – Data Preview**

- Displays a preview of the selected table.
- For the **Orders** table, visible columns include:
  - `Row ID`, `Order ID`, `Order Date`, `Ship Date`, `Ship Mode`, `Customer Name`, etc.
- The preview is read-only and lets you verify the correct table before loading.

---

## Navigation Buttons (Bottom of Window)

- **Load**  
  Loads the selected tables directly into Power BI and displays them in the Fields pane.

- **Transform Data**  
  Opens **Power Query Editor** for cleaning, shaping, or transforming data (changing data types, removing columns, filtering rows, etc.).

- **Cancel**  
  Closes the Navigator without loading anything.

---

## Workflow Stage

This screen represents **Step 1** of building a Power BI report:

1. Open Power BI Desktop  
2. Go to **Home → Excel workbook**  
3. Select the file (`orders.xlsx`)  
4. Use the **Navigator Window** (the screen shown) to:
   - Select tables (Orders/People/Returns)
   - Either **Load** or **Transform Data**

After this step, you proceed to:
- Build relationships between tables  
- Add visuals to the report canvas  
- Create analyses, dashboards, or KPIs  

---

## 📌 Step 2: Create a Ribbon Chart From the Excel Sheet
1. Go to **Report View**.
2. From **Visualizations**, select **Ribbon Chart**.
3. Drag **Category** → *Axis*.
4. Drag your numeric value field (e.g., *Sales*, *Amount*, or similar) → *Values*.
5. Drag **Category** again → *Legend* (if required).
6. Format the chart (colors, labels, title).

<img width="1919" height="1024" alt="two" src="https://github.com/user-attachments/assets/9d58fd62-72f4-4feb-8681-57f4f5c246b9" />

The visual shown is a **Ribbon Chart** in Power BI. This chart compares multiple measures across different categories and highlights which measure ranks highest within each category.

### What the Chart Displays
- **X-axis:** Product *Category* (Technology, Furniture, Office Supplies)
- **Y-axis:** Combined values of  
  - Sum of Sales  
  - Sum of Profit  
  - Sum of Quantity
- **Legend:** Shows the three measures being compared:
  - Sum of Sales (blue)
  - Sum of Profit (dark blue)
  - Sum of Quantity (orange)

### How a Ribbon Chart Works
- Each category is represented by vertical segments.
- The **width and height of the ribbons** represent the magnitude of each measure.
- The **top ribbon** indicates the highest-ranking measure within that category.
- This makes it easy to compare which measure leads in each category and how rankings change.

### Fields Used
- **X-axis:** Category  
- **Y-axis:** Sum of Sales, Sum of Profit, Sum of Quantity  
- **Legend:** Measures (Sales, Profit, Quantity)

### Purpose
This chart helps visualize:
- Which performance metric dominates each category.
- How sales, profit, and quantity compare side-by-side.
- Changes in ranking across categories.

---

## 📌 Step 3: Create a Line Chart From the Excel Sheet
1. Select **Line Chart** from **Visualizations**.
2. Drag **Category** → *Axis*.
3. Drag your numeric column → *Values*.
4. Format the line chart as needed.

<img width="1914" height="1028" alt="three" src="https://github.com/user-attachments/assets/c7fc73e5-8a38-4946-b056-e50a06e4ab68" />


---

## 📌 Step 4: Create an Area Chart From the Excel Sheet
1. Select **Area Chart** from **Visualizations**.
2. Drag **Category** → *Axis*.
3. Drag your numerical measure → *Values*.
4. Adjust formatting.

<img width="1916" height="1034" alt="Four" src="https://github.com/user-attachments/assets/49549266-c43c-4e7e-b225-3c5094bc289e" />


