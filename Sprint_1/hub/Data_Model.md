

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

## Visual Example
<img width="1675" height="996" alt="image" src="https://github.com/user-attachments/assets/5ba1850d-7ffa-4ac6-a52d-304f19976a7a" />

---

# 🧩 **XYZ Company Employee & Training Dashboard**



Executive Summary: This report provides an in-depth Power BI dashboard design for XYZ Company’s employee and training data (from Data_Model.xlsx). It visualizes key metrics such as headcount by department and location, training participation and status, training course popularity, and salary distributions. For example, a bar chart compares the number of employees in each department (highlighting differences at a glance
ethanguyant.com
), while a stacked chart breaks down training applications into completed vs. pending. We also include city-by-department matrices and designation breakdowns. All charts use DAX measures (COUNTROWS, SUM, CALCULATE, etc.) based on the provided fields. Report pages will feature department and city slicers to filter all visuals, and consistent color theming and data labels for clarity.

Key Findings (Example): The Operations (DEP1) and Payroll (DEP3) departments have the smallest headcounts, whereas IT (DEP4) and Workforce Mgmt (DEP2) are largest. “Cyber Security Training” has the highest number of applications; “Tableau” the least. About 43% of all assigned trainings are completed and 57% are pending. Salary totals are highest in IT and for higher-level designations. These insights will appear as charts on dedicated report pages.

Data Model and Assumptions

Tables and Keys: We assume a star-schema model. Department (DEPT_CODE, DEPT_Name) is a dimension (one-side of relationships)
learn.microsoft.com
. EMP_SAL (EID, DEPT CODE, SALARY, DESIGNATIONS) and Training Status (EID, Training, STATUS) act as fact tables (many-side). EMP_Details (EID, Name, City, etc.) is a dimension table linked one-to-one to EMP_SAL by EID. Trainings (Name of the training, Pricing) is a training dimension linked by training name. Relationships:

Department[DEPT_CODE] → EMP_SAL[DEPT CODE] (1:Many)

EMP_SAL[EID] → EMP_Details[EID] (1:1)

EMP_SAL[EID] → Training Status[EID] (1:Many)

Trainings[Name of the training] → Training Status[Training] (1:Many)
(Thus, Department and Training tables filter the facts.) This follows star schema best-practice where the “one” side is dimension and the “many” side is fact
learn.microsoft.com
.

Field Interpretation: We treat ADDRESS in EMP_Details as the employee’s City. In EMP_SAL, DESI AS ON JAN 19 is the previous designation (used in Q7) and CURRENT DESI is the current job title. All measures below use these exact field names.

Data Quality Assumptions: We assume EID is unique per employee. We note some data cleanup may be needed (see Power Query section). Minor spelling issues (e.g. “Gurgaoan” vs “Gurgaon”, “Security Training” vs “Cyber Security Training”, inconsistent designation capitalization) should be corrected in the model.

Power Query / Data Preparation

Rename and Correct Columns: Rename the Trainigs table to Trainings for consistency. Ensure column names have no unwanted spaces. In EMP_SAL, you may rename DESI AS ON JAN 19 to something simpler (e.g. Prev Designation) if desired.

Data Type Fixes: Convert DOB and DOJ in EMP_Details to Date data type (the raw Excel has mixed formats). Ensure SALARY is numeric.

Standardize Text: In Training Status, change “Security Training” to “Cyber Security Training” so it matches the Trainings table. Clean up city names in EMP_Details (e.g. merge “Gurgaoan” to “Gurgaon”). Normalize designation text (make case consistent) or create a lookup table for designations.

Dimension Creation: If needed, split EMP_Details[ADDRESS] into separate City and (if present) State fields. Create lookup (dimension) tables for City and Designation if the model benefits from it (not strictly required for these charts).



### 🔹 **Data_Model_Related_Report**
* Click this below link where we can get a clear report of a Comany*
* [Click Here](https://app.powerbi.com/links/BA_l-M01AR?ctid=66c5e13f-8c43-4359-b2e8-51775c6d298d&pbi_source=linkShare)


---

