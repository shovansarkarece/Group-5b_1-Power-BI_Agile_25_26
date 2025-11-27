

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

# 1. Executive summary

- This report visualizes training and employee data for the XYZ company. It answers the core business questions:

- #### Number of employees per department

- #### Number of trainings applied per department

- #### Out of applied trainings: how many completed and how many pending

- #### Courses applied most/least times

- #### City-wise and department-wise counts of employees

- #### Number of each training done for each department

- #### Number of employees under each designation (current)

- #### Total salary by department

- #### Total salary by designation

## This report provides an in-depth Power BI dashboard design for XYZ Company’s employee and training data (from Data_Model.xlsx).

- #### It visualizes key metrics such as:

    - #### Headcount by department and location

    - #### Training participation and status

    - #### Training course popularity

    - #### Salary distributions

- #### A bar chart compares the number of employees in each department

- #### A stacked chart breaks down training applications into completed vs. pending

- #### A city-by-department matrix shows geographical distribution

- #### Designation breakdowns provide historical role insights

- #### All charts use DAX measures like COUNTROWS, SUM, CALCULATE, etc.



# 2. Data model (assumptions)

- #### Tables expected in ```Data_Model.xlsx```:

- #### ```Employees``` (EmployeeID, FullName, DepartmentID, DesignationID, CityID, Salary, HireDate, Status)

- #### ```Departments``` (DepartmentID, DepartmentName)

- #### ```Designations``` (DesignationID, DesignationName)

- #### ```Cities``` (CityID, CityName)

- #### ```Trainings``` (TrainingID, TrainingName, CourseCode, CourseCategory)

- #### ```TrainingApplications``` (ApplicationID, EmployeeID, TrainingID, AppliedDate, CompletionDate, Status)

# Relationships (one-to-many):

- #### Departments[DepartmentID] → Employees[DepartmentID]

- #### Designations[DesignationID] → Employees[DesignationID]

- #### Cities[CityID] → Employees[CityID]

- #### Employees[EmployeeID] → TrainingApplications[EmployeeID]

- #### Trainings[TrainingID] → TrainingApplications[TrainingID]

### 🔹 **Data_Model_Related_Report**

* Click this below link where we can get a clear report of a Comany*

* [Click Here](https://app.powerbi.com/links/BA_l-M01AR?ctid=66c5e13f-8c43-4359-b2e8-51775c6d298d&pbi_source=linkShare)


---

