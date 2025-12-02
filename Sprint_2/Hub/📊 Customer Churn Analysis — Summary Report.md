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

* Average monthly bill: **$64.76**
* Customers with higher bills tend to churn more

### 📌 **Total Charges**

* Highly skewed distribution
* High-value (long tenure) customers churn far less

---

## 🔹 **4. Churn Drivers —- Correlations**

| Feature        | Correlation with Churn | Interpretation                      |
| -------------- | ---------------------- | ----------------------------------- |
| Tenure         | **-0.35**              | Longer tenure → lower churn         |
| TotalCharges   | **-0.20**              | Higher lifetime value → lower churn |
| MonthlyCharges | **+0.19**              | Expensive plans → more churn        |
| SeniorCitizen  | **+0.15**              | Seniors churn more                  |

---
## 🔹 **5. Churn by Categorical Features**

### 📌 **Contract Type**
