# Power BI Dummy Data Project

This repository contains three realistic dummy datasets and two Power BI dashboards created for academic practice.

---

## ✅ Checklist Overview

- [x] Create **3 different dummy datasets** (Sales, HR, Operations)
- [x] Ensure **each dataset has 500–1,000 rows** with realistic values
- [x] Include **multiple related tables** for each dataset (fact + dimension tables)
- [x] Create a **data dictionary** for each dummy dataset explaining columns and relationships
- [x] Save datasets in **multiple formats** (Excel, CSV)
- [x] Validate **data quality** (no nulls in key fields, proper data types, referential integrity)
- [x] Create **2 complete dashboards** with at least 5–7 visuals each
- [x] Document the **business scenario / story** behind each dashboard

---

## 1. Datasets Overview

### 1.1 Retail Sales Dataset

**Business context:**  
Mid‑size retail company selling products across multiple regions and channels (online & store).

**Tables**
- `Sales_Fact`
- `Dim_Date`
- `Dim_Product`
- `Dim_Customer`
- `Dim_Store`

**Row volume**
- `Sales_Fact`: ~900 rows  
- Each dimension table: 50–300 rows

**Key relationships**
- `Sales_Fact[DateKey]` → `Dim_Date[DateKey]`
- `Sales_Fact[ProductKey]` → `Dim_Product[ProductKey]`
- `Sales_Fact[CustomerKey]` → `Dim_Customer[CustomerKey]`
- `Sales_Fact[StoreKey]` → `Dim_Store[StoreKey]`

---

### 1.2 HR & Employee Dataset

**Business context:**  
Company wants to monitor headcount, hiring, attrition and performance across departments and locations.

**Tables**
- `Employee_Fact`
- `Dim_Employee`
- `Dim_Department`
- `Dim_Location`
- `Dim_Date` (shared with other models if needed)

**Row volume**
- `Employee_Fact`: ~650 rows  
- Dimension tables: 30–150 rows

**Key relationships**
- `Employee_Fact[EmployeeKey]` → `Dim_Employee[EmployeeKey]`
- `Employee_Fact[DeptKey]` → `Dim_Department[DeptKey]`
- `Employee_Fact[LocationKey]` → `Dim_Location[LocationKey]`
- `Employee_Fact[DateKey]` → `Dim_Date[DateKey]`

---

### 1.3 Operations & Inventory Dataset

**Business context:**  
Warehouse operations team tracks inventory levels, purchase orders, and stock movements.

**Tables**
- `Inventory_Fact`
- `Dim_Item`
- `Dim_Supplier`
- `Dim_Warehouse`
- `Dim_Date`

**Row volume**
- `Inventory_Fact`: ~750 rows  
- Dimension tables: 40–200 rows

**Key relationships**
- `Inventory_Fact[ItemKey]` → `Dim_Item[ItemKey]`
- `Inventory_Fact[SupplierKey]` → `Dim_Supplier[SupplierKey]`
- `Inventory_Fact[WarehouseKey]` → `Dim_Warehouse[WarehouseKey]`
- `Inventory_Fact[DateKey]` → `Dim_Date[DateKey]`

---

## 2. Data Dictionaries (Summary)

> Full detailed data dictionaries can be kept as separate files:  
> `/data_dictionaries/sales_data_dictionary.xlsx`  
> `/data_dictionaries/hr_data_dictionary.xlsx`  
> `/data_dictionaries/operations_data_dictionary.xlsx`

### 2.1 Retail Sales – Example Columns

**Sales_Fact**
- `SalesID` – Surrogate primary key  
- `DateKey` – Links to `Dim_Date`  
- `ProductKey` – Links to `Dim_Product`  
- `CustomerKey` – Links to `Dim_Customer`  
- `StoreKey` – Links to `Dim_Store`  
- `Quantity` – Units sold  
- `UnitPrice` – Price per unit  
- `DiscountAmount` – Discount per transaction  
- `TotalSales` – Calculated as `(Quantity * UnitPrice) - DiscountAmount`

**Dim_Product**
- `ProductKey` – Surrogate primary key  
- `ProductName` – Product description  
- `Category` – Product category  
- `SubCategory` – Product sub-category  
- `UnitCost` – Cost price  
- `IsActive` – Active/inactive flag

_(Similar structures are defined for HR and Operations in their data dictionary files.)_

---

## 3. File Formats

Each dataset is saved in:  

- **Excel**: `./data/excel/`  
  - `sales_dataset.xlsx`  
  - `hr_dataset.xlsx`  
  - `operations_dataset.xlsx`  

- **CSV**: `./data/csv/`  
  - `sales_fact.csv`, `dim_product.csv`, etc.  
  - `employee_fact.csv`, `dim_department.csv`, etc.  
  - `inventory_fact.csv`, `dim_item.csv`, etc.

---

## 4. Data Quality & Validation

The following checks were applied before loading into Power BI:

- No **NULL values** in key fields (`*Key`, IDs, and joins)
- Data types verified:
  - Date columns → `Date`
  - Numeric measures → `Decimal / Whole number`
  - Categorical fields → `Text`
- Referential integrity:
  - Every foreign key in fact tables has a **matching key** in related dimension tables
- No negative quantities for sales or inventory
- Business logic sanity checks:
  - `TotalSales >= 0`
  - Employee hire dates not in the future
  - Inventory on hand cannot be negative

---

## 5. Dashboards

### 5.1 Dashboard 1 – Retail Sales Performance

**Business scenario / story:**  
Management wants to understand how sales are performing across time, products, and regions to support pricing and promotion decisions.

**Main questions answered**
- Which **regions and stores** are generating the highest revenue?
- What are the **monthly and quarterly trends** of total sales?
- Which **products / categories** drive most of the revenue and profit?
- How do **discounts** impact sales volume and margin?

**Visuals (5–7 visuals)**
1. Line chart – **Total Sales by Month**  
2. Clustered column chart – **Sales by Region and Store**  
3. Tree map – **Sales by Product Category & Subcategory**  
4. Bar chart – **Top 10 Products by Sales**  
5. Card visuals – **Total Sales, Total Quantity, Average Discount**  
6. Stacked column chart – **Sales vs. Profit by Category**  
7. Slicer panel – **Filters for Year, Region, Category, Channel**

---

### 5.2 Dashboard 2 – HR & Operations Insights

**Business scenario / story:**  
HR and operations leadership want a combined view of workforce trends and warehouse efficiency to support capacity planning.

**Main questions answered**
- How is **headcount** changing over time by department and location?
- What is the **attrition rate** and which departments are most affected?
- How does **warehouse inventory** support demand (stock-outs vs. overstock)?
- Which **suppliers** have the highest order volume?

**Visuals (5–7 visuals)**
1. Line chart – **Headcount over Time by Department**  
2. Bar chart – **Attrition Count / Rate by Department**  
3. Donut chart – **Employee Distribution by Location**  
4. Table – **Employee List with Key KPIs (Tenure, Performance Rating)**  
5. Column chart – **Inventory Levels by Warehouse & Item Category**  
6. Matrix – **Supplier vs. Total Order Quantity & Value**  
7. KPI cards – **Total Headcount, Attrition Rate, Average Inventory Days**

---

## 6. Power BI Setup Instructions

1. Open **Power BI Desktop**.
2. Click **Get Data → Text/CSV** or **Excel** and load files from the `./data/` folder.
3. In **Model view**, confirm relationships between fact and dimension tables as described above.
4. Create measures in DAX (examples):
   - `Total Sales = SUM(Sales_Fact[TotalSales])`
   - `Total Quantity = SUM(Sales_Fact[Quantity])`
   - `Attrition Rate = DIVIDE([Leavers], [Average Headcount])`
5. Build visuals according to the dashboard descriptions.
6. Save the Power BI file as `PowerBI_Dummy_Project.pbix` in the root of the repository.

---

## 7. Folder Structure (Proposed)

```text
.
├── data
│   ├── csv
│   └── excel
├── data_dictionaries
├── pbix
│   └── PowerBI_Dummy_Project.pbix
└── README.md   ← (this file)
```

You can customize the datasets, visuals, and measures further based on professor guidelines or project requirements.

