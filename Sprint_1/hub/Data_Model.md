

# 📘 **What is Data Modelling?**

**Data Modelling** is the process of **structuring and organizing data** so it becomes easy to store, manage, retrieve, and analyze.
It defines **what data your system needs**, **how different data elements relate**, and **how they should be stored in a database or analytical model**.

Think of it as **creating a blueprint** before building a database or dashboard.
## Visual Example
<img width="1584" height="1472" alt="Data_Modeling" src="https://github.com/user-attachments/assets/3a35015f-b3b8-46d7-b40a-52c1bb55890c" />

---

# ✅ **Why Do We Use Data Modelling?**

* To ensure **data accuracy** (fewer errors)
* To remove **duplicate data**
* To make queries **faster**
* To support **analytics and reporting** efficiently
* To ensure **consistent** and **organized** data across the system
* To define clear **relationships** between tables
## Visual Example-->(i)
<img width="512" height="411" alt="conceptual_erd_27340" src="https://github.com/user-attachments/assets/73129a3e-94fd-4edd-ab75-6e50b4085e10" />

## Visual Example-->(ii)
<img width="1475" height="802" alt="create-manage-relationships-01" src="https://github.com/user-attachments/assets/c17762fe-c00b-4f20-92e5-cce318b8a319" />

---

# 🧱 **Types of Data Models**

## 1️⃣ **Conceptual Data Model (High-level)**

* Shows **entities** (Customer, Product, Order)
* Shows **high-level relationships**
* Used by business stakeholders
* No technical details
* 
## Visual Example
<img width="1536" height="1024" alt="Types_Data_Model" src="https://github.com/user-attachments/assets/3077da88-081f-4826-bc35-e82662d8b2c3" />

---

## 2️⃣ **Logical Data Model (Detailed)**

* Adds **attributes/columns**
* Introduces **primary keys** and **foreign keys**
* Still does *not* include DB engine details
## Visual Example
![logical-data-model](https://github.com/user-attachments/assets/5731520a-485e-4640-bb9c-71dcf8711fdb)

---

## 3️⃣ **Physical Data Model (Database-level)**

* Shows **actual tables**
* Contains **data types (INT, VARCHAR)**
* Indexes, constraints, keys
* Used by developers and DBAs
## Visual Example==>(i)
![Physical_Data_model_e-commerce](https://github.com/user-attachments/assets/df0e0190-4285-4575-af8e-d8a2ec1dc302)

## Visual Example==>(ii)
![physicalDataModel](https://github.com/user-attachments/assets/a216afb2-553f-460c-b177-08c0cea4a1db)

---

# 📊 **Data Modelling in Power BI**

Power BI uses **Star Schema**, which includes:

### ⭐ **Fact Table**

* Contains **numeric values** (Sales Amount, Quantity)
* Contains **foreign keys**

### 🔷 **Dimension Tables**

* Contains descriptive information
  (Date, Customer, Product, Region)

## Visual Example==>(i)
![star-schema-example-1](https://github.com/user-attachments/assets/36bdd538-0419-4976-8e5f-7b04dd893f61)

## Visual Example==>(ii)
<img width="1675" height="996" alt="image" src="https://github.com/user-attachments/assets/5ba1850d-7ffa-4ac6-a52d-304f19976a7a" />

---

# 🧩 **Common Data Modelling Concepts**

### 🔹 **Primary Key (PK)**

A unique identifier for a row.

### 🔹 **Foreign Key (FK)**

Links two tables.

### 🔹 **One-to-Many Relationship (1:* )**

Most common in Power BI.

### 🔹 **Normalization**

Organizing data to reduce redundancy.

### 🔹 **Denormalization**

Combining data for faster analytics.

---

