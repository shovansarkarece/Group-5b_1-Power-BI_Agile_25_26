# 🔶 What is Denormalization?

Denormalization is the process of intentionally adding redundancy into a database to improve read performance, especially for reporting, analytics, dashboards, and OLAP systems.

👉 In normalization, we split data into multiple related tables to reduce redundancy.

👉 In denormalization, we combine tables or duplicate data to make querying faster and simpler.

### In simple terms:

> Normalization = less redundancy → more joins
>
> Denormalization = fewer joins → faster queries

# 🔶 **Why Do We Use Denormalization?**

Because in analytics and reporting systems (like **Power BI, OLAP cubes**), users expect **fast read performance**, and those systems often query **large tables** many times.

Denormalization helps by:

* Reducing number of joins
* Improving query speed
* Simplifying data models
* Making star-schema fact tables easier to use

---

# 🔶 **Techniques of Denormalization**

Here are the common methods:

### **1️⃣ Combine Tables (Merging)**

Merge two normalized tables into one to avoid joins.
Example: Customer table + Address table merged.

### **2️⃣ Add Redundant Columns**

Store calculated or repeated values to reduce computation.
Example: Store "Total Order Amount" in fact table instead of recalculating.

### **3️⃣ Pre-Computed Aggregations**

Store monthly sales, yearly totals, etc., instead of computing every time.

### **4️⃣ Add Lookup Values Inside Fact Table**

Instead of using many dimension tables, store descriptive fields inside fact table.

---

# 🔶 **Use Cases of Denormalization (Very Important for Power BI)**

## ⭐ **Use Case 1: Reporting and Dashboards**

Dashboards (Power BI/Tableau) need **fast read performance**.
If data is heavily normalized, each visual would perform many joins → slow.

👉 Solution: Denormalize into a **Star Schema** (Fact + Dimensions).

**Example:**

* FactSales (Denormalized)
* DimCustomer
* DimProduct
* DimDate

This gives faster visuals and better compression.

---

## ⭐ **Use Case 2: OLAP Systems (Data Warehousing)**

OLTP → Normalized
OLAP → Denormalized

**Why?**
OLAP focuses on **read-heavy** operations and aggregations.

Typical denormalized structures:

* Star Schema
* Snowflake Schema (semi-normalized)
* Wide Tables (big tables with many columns)

---

## ⭐ **Use Case 3: Reducing Expensive Joins in Big Data**

When data size is huge, joins cost a lot of time and memory.

**Example:**
A 500M row fact table joining 6 dimension tables.
Denormalizing 1–2 dimensions into the fact table improves performance.

---

## ⭐ **Use Case 4: Pre-Computed Columns for Optimization**

Instead of calculating columns repeatedly in your queries or DAX:

Examples:

* TotalAmount = Quantity × Price
* Age = CurrentYear − BirthYear
* FullName = FirstName + LastName

Storing these results saves processing time.

---

## ⭐ **Use Case 5: Materialized Views / Summary Tables**

Create summary tables for faster dashboard performance.

Examples:

* Sales by Month
* Sales by Region
* Inventory by Category

These "summary tables" are a form of denormalization.

---

## ⭐ **Use Case 6: Flattening JSON or Semi-Structured Data**

When working with API data or logs, flattening nested JSON into a wide table is denormalization.

---

# 🔶 **When You Should NOT Denormalize**

Avoid denormalization when:
❌ Data changes very frequently
❌ You need strict update consistency
❌ Disk space is very limited
❌ Complex write-heavy systems (OLTP)

---

# 🔶 **Small Example to Make It Very Easy**

### **Normalized (3 tables)**

* Orders
* Customers
* Products

To display a report:
You must join Orders → Customers → Products.

### **Denormalized (1 wide table)**

* OrderID
* CustomerName
* CustomerCity
* ProductName
* ProductCategory
* OrderAmount

No joins → Faster queries.

---

# 🔶 **One-Line Summary**

**Denormalization makes databases faster for reading by adding redundancy and reducing joins—very useful for analytics, reporting, and Power BI data models.**

---

If you want, I can also create:
✅ A **Mermaid ER diagram** showing denormalization
✅ A **Markdown snippet** for GitHub
✅ A **real-world case study** (e.g., e-commerce, banking, healthcare)

Would you like that?




```mermaid
flowchart LR
    subgraph Normalized
        direction TB
        CUST[Customer\nCustomerID PK\nFirstName\nLastName\nEmail]
        ADDR[Address\nAddressID PK\nCustomerID FK\nStreet\nCity\nCountry]
        ORD[Orders\nOrderID PK\nCustomerID FK\nAddressID FK\nOrderDate]
        OI[OrderItems\nOrderItemID PK\nOrderID FK\nProductID FK\nQuantity\nUnitPrice]
        PROD[Products\nProductID PK\nProductName\nCategory\nPrice]

        CUST --> ADDR
        CUST --> ORD
        ORD --> OI
        PROD --> OI
    end

    subgraph Denormalized
        direction TB
        FACT[SALES_FACT\nOrderID PK\nOrderDate\nCustomerID\nCustomerFullName\nCustomerCity\nCustomerCountry\nProductID\nProductName\nProductCategory\nUnitPrice\nQuantity\nTotalAmount]
    end

    Normalized --> Denormalized

```
