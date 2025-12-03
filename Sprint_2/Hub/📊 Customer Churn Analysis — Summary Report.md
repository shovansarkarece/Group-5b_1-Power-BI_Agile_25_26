
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

### 📌 *Tenure*

* Average tenure: **32.4 months**
* New customers (0–12 months) have the **highest churn**

### 📌 *Monthly Charges*
* Average monthly bill: **$64.76**
* Customers with higher bills tend to churn more

### 📌 *Total Charges*

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

### 📌 *Contract Type*

* Month-to-month → **~44% churn**
* One-year → ~10% churn
* Two-year → ~3% churn
  ➡️ **Contract type is the strongest churn predictor**

### 📌 *Internet Service*

* Fiber optic → **high churn (~42%)**
* DSL → moderate
* No internet → very low churn (~6%)

### 📌 *Payment Method*

* Electronic check → **highest churn (~45%)**
* Auto-pay (bank transfer/credit card) → **lowest churn (~15%)**

### 📌 *Support Services*
* Electronic check → **highest churn (~45%)**
* Auto-pay (bank transfer/credit card) → **lowest churn (~15%)**

### 📌 *Support Services*

Customers who have the following churn much less:

* Online Security
* Tech Support
* Device Protection

➡️ Optional services **improve retention**

---

## 🔹 **6. Behavioral Patterns Found**

* New, low-tenure customers are most at risk
* Customers with **high monthly bills** churn more
* Auto-pay customers are more loyal
* Customers with **multiple add-ons** churn less
* Senior citizens and single customers churn more

---
## 🔹 **7. Recommended Business Actions**

* Convert month-to-month users to 1–2 year contracts
* Promote auto-pay options
* Offer discounts to fiber-optic customers (high-risk group)
* Bundle add-on services (security, support, backup)
* Improve onboarding for new customers (tenure < 3 months)

---

# 📊 **8. Power BI Dashboard Design (Step-by-Step)**

## 🟦 **Power BI Page 1 — Overview Dashboard**

**Visuals:**

* Card: Total Customers
* Card: Total Churn
* Card: Churn Rate
* Gauge: Churn (%)
* Bar Chart: Churn vs No Churn
* KPI: Avg Tenure, Avg Monthly Charge

---

## 🟩 **Power BI Page 2 — Churn Segmentation**

**Visuals:**

* Bar chart: Churn % by Contract
* Bar chart: Churn % by Internet Service
* Bar chart: Churn % by Payment Method
* Matrix: Churn by Gender, Senior Citizen, Partner, Dependents
* Slicers: Contract, SeniorCitizen, PaymentMethod, Gender

---

## 🟧 **Power BI Page 3 — Customer Value Insights**

**Visuals:**

* Histogram: Monthly Charges
* Histogram: Total Charges
* Boxplot: Monthly Charges vs Churn
* Line chart: Churn rate by Tenure
* Scatter: MonthlyCharges vs TotalCharges (churn colored)

---

## 🟨 **Power BI Page 4 — Churn Drivers (ML Page)**

**Visuals:**

* Feature importance table
* Waterfall: Risk factors
* Heat map: Churn % by (Contract × PaymentMethod)

---

# 🧮 **9. Important DAX Measures**

```DAX
Total Customers = COUNTROWS('Customers')
Churned Customers = CALCULATE(COUNTROWS('Customers'), 'Customers'[Churn] = "Yes")
Churn Rate = DIVIDE([Churned Customers], [Total Customers])
Avg Tenure = AVERAGE('Customers'[tenure])

Avg Monthly Charges = AVERAGE('Customers'[MonthlyCharges])

Total Revenue = SUM('Customers'[TotalCharges])
```

---

# 📥 **10. Files You Should Export From This Analysis**
You should include:

* `churn_analysis.md` → your report file
