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

*Screenshot showing the process of uploading the data on Power BI -*
<img width="1919" height="1079" alt="SS-1" src="https://github.com/user-attachments/assets/7f820fa1-af0f-42b4-b027-1f4dbc594849" />

<img width="1918" height="1030" alt="SS-2" src="https://github.com/user-attachments/assets/1346bb1e-3b36-4364-b62d-80e45c59fb40" />

STEP 2 — Clean Column Types

In the Power Query Editor:

* Ensure ID fields are text
* Ensure dates are date type
* Ensure numeric fields (Effort, MaxPrice, DaysOffered) are numbers

Click Close & Apply












