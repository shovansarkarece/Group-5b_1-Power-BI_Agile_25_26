# 📊 Customer Churn Analysis — Summary Report

## 🔹 **1. Dataset Overview**

* Total records: **7,043 customers**
* Total columns: **21 features**
* Data types:

  * **Numeric:** SeniorCitizen, Tenure, MonthlyCharges, TotalCharges
  * **Categorical:** Gender, Partner, Dependents, PhoneService, InternetService, Contract, PaymentMethod, etc.
* Missing values:

  * **11 missing TotalCharges**, all belonging to **tenure = 0** customers → imputed as **0**
---

## 🔹 **2. Churn Overview**

* Churn column: **Yes / No**
* Churn count:

  * **Churned:** 1,869
  * **Stayed:** 5,174
 
* Overall churn rate: **~26.5%**
* Industry benchmark: telecom churn often reaches **25%–30%**

---

## 🔹 **3. Key Numerical Insights**

### 📌 **Tenure**

* Average tenure: **32.4 months**
* New customers (0–12 months) have the **highest churn**

### 📌 **Monthly Charges**
