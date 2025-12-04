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
4. Select all sheets:

A Navigator window appears showing all sheets in your Excel file

You should see checkboxes next to each sheet name:

☑ Assignments

☑ Contracts

☑ ContractRoles

☑ Employees

☑ Offers

☑ Projects

☑ Providers

☑ ServiceRequests

☑ Skills

Check the box next to EACH sheet (or check the box at the very top to select all)

*Screenshot showing the process of uploading the data on Power BI -*

<img width="1919" height="1079" alt="SS-1" src="https://github.com/user-attachments/assets/7f820fa1-af0f-42b4-b027-1f4dbc594849" />

<img width="1918" height="1030" alt="SS-2" src="https://github.com/user-attachments/assets/1346bb1e-3b36-4364-b62d-80e45c59fb40" />

<img width="1918" height="1027" alt="image" src="https://github.com/user-attachments/assets/98e8d3bb-5bb2-4b24-8a79-8c51715019e4" />

STEP 2 — Clean Column Types

In the Power Query Editor:

* Ensure ID fields are text
* Ensure dates are date type
* Ensure numeric fields (Effort, MaxPrice, DaysOffered) are numbers

Click Close & Apply

STEP 3 — Create Relationships

Go to:
➡ Model View

1. On the far left side of Power BI Desktop, you'll see three icons stacked vertically:

📊 Report view (top)

📋 Table view (middle)

🔗 Model view (bottom)

2. Click the bottom icon (Model view) - it looks like connected boxes

You'll now see all your tables displayed as boxes with column names listed inside them.

*Screenshot showing the Model View of the data -*

<img width="1919" height="1029" alt="SS-3 from PowerBI_Dummy_Data-2" src="https://github.com/user-attachments/assets/5fa054bb-3ad3-4cd9-9028-63a652036f94" />

Now create these relationships:

**What is a relationship?**

A relationship connects two tables so Power BI knows how they're linked (like "this employee worked on this project").

**How to create a relationship:**

1. Drag and drop a column from one table onto a matching column in another table
2. A line will appear connecting them
3. A settings window will pop up

Let me show each relationship to create:

🔗 **Relationship 1: Assignments → Employees**

1. Find the Assignments table box
2. Find the column EmployeeID inside it
3. Click and hold on EmployeeID
4. Drag to the Employees table
5. Drop it on the EmployeeID column in the Employees table
6. A "Create relationship" window opens:

      * From table: Assignments
      * From column: EmployeeID
      * To table: Employees
      * To column: EmployeeID
      * Cardinality: Select "Many to one (*:1)"
      * Cross filter direction: Select "Single"

7. Click OK

*Screenshot showing Assignments and Employees tables -*

<img width="509" height="322" alt="image" src="https://github.com/user-attachments/assets/16eefba3-76ac-49e1-b89b-7a67955c8c77" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="679" height="766" alt="image" src="https://github.com/user-attachments/assets/1ed0e44d-fd95-4949-9936-aa3b510b5eaa" />

*Screenshot showing the relation created between Assignments and Employees -*

<img width="525" height="358" alt="image" src="https://github.com/user-attachments/assets/012600f1-b13d-468d-bad0-fc54dd1df46f" />

🔗 **Relationship 2: Assignments → Projects**

1. In Assignments table, find ProjectID
2. Drag it to ProjectID in the Projects table
3. In the settings window:

      * Cardinality: "Many to one (*:1)"
      * Cross filter direction: "Single"

4. Click OK

*Screenshot showing Assignments Employees and Projects tables -*

<img width="522" height="468" alt="image" src="https://github.com/user-attachments/assets/9298a04c-e20b-4488-b3c7-beef377ac654" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="622" height="850" alt="image" src="https://github.com/user-attachments/assets/df5537b6-c6ab-471c-9ead-23893700de79" />

*Screenshot showing the relation created between Assignments and Projects -

<img width="527" height="557" alt="image" src="https://github.com/user-attachments/assets/b936d917-908c-417a-b885-5773ff095f24" />

🔗 **Relationship 3: ServiceRequests → Projects**

1. In ServiceRequests table, find ProjectID
2. Drag it to ProjectID in the Projects table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

*Screenshot showing ServiceRequests and Projects tables -*

<img width="540" height="293" alt="image" src="https://github.com/user-attachments/assets/5ec99332-95a6-489e-ba19-5ae6af2c2f29" />




🔗 **Relationship 4: ServiceRequests → Contracts**

1. In ServiceRequests table, find ContractID
2. Drag it to ContractID in the Contracts table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

🔗 **Relationship 5: ServiceRequests → Employees**

1. In ServiceRequests table, find RequestedBy
2. Drag it to EmployeeID in the Employees table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

🔗 **Relationship 6: Offers → Providers**

1. In Offers table, find ProviderID
2. Drag it to ProviderID in the Providers table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

🔗 **Relationship 7: Offers → ServiceRequests**

1. In Offers table, find RequestID
2. Drag it to RequestID in the ServiceRequests table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

🔗 **Relationship 8: Skills → Employees**

1. In Skills table, find EmployeeID
2. Drag it to EmployeeID in the Employees table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

🔗 **Relationship 9: ContractRoles → Contracts**

1. In ContractRoles table, find ContractID
2. Drag it to ContractID in the Contracts table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK













