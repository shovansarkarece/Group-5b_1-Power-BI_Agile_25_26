## **Power BI Dashboard-1 Guide**
---

Let’s build:

✅ 1. The Power BI Data Model (Star Schema)

✅ 2. Step-by-Step instructions to create it in Power BI Desktop

✅ 3. Recommended relationships

✅ 4. DAX measures

✅ 5. Dashboard layout

---
### ⭐ 1. Data Model (Star Schema)
---
Dataset contains three fact tables:

Fact Tables -

1. Assignments
2. ServiceRequests
3. Offers

Dimension Tables -

* Employees
* Skills
* Projects
* Contracts
* ContractRoles
* Providers
* Date table (Calendar)

### ⭐ 2. Ideal Relationship Diagram
---
Below is the exact model we will build:

      DimEmployees            DimProjects             DimContracts          DimProviders
            |                        |                        |                     |
            |                        |                        |                     |
      FactAssignments         FactServiceRequests        FactOffers---------------/
            |                        |                        |
            |                        |                        |
       DimSkills               DimContractRoles         DimDate (Calendar)

### ⭐ 3. Step-by-Step: Create the Data Model in Power BI
---
STEP 1 — Load Excel file

1. Open Power BI Desktop
2. Click Get Data → Excel
3. Choose PowerBI_Dummy_Data-2.xlsx
4. Select all sheets


















