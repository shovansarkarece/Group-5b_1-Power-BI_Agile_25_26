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

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="677" height="766" alt="image" src="https://github.com/user-attachments/assets/30949789-a188-4543-80b9-59fe05491a12" />

*Screenshot showing the relation created between ServiceRequests and Projects -

<img width="628" height="658" alt="image" src="https://github.com/user-attachments/assets/a69ddc7d-625d-4849-b529-1ef5d9514dab" />

🔗 **Relationship 4: ServiceRequests → Contracts**

1. In ServiceRequests table, find ContractID
2. Drag it to ContractID in the Contracts table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

*Screenshot showing ServiceRequests and Contracts tables -*

<img width="479" height="274" alt="image" src="https://github.com/user-attachments/assets/888e6f91-310a-4dde-bf04-b51ff6ce05e3" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="667" height="750" alt="image" src="https://github.com/user-attachments/assets/b416342f-e651-4965-80c7-cbb47729e3df" />

*Screenshot showing the relation created between ServiceRequests and Contracts -

<img width="567" height="277" alt="image" src="https://github.com/user-attachments/assets/b3ac7242-ab3f-4230-b85a-431e3dc43bf9" />

<img width="749" height="612" alt="image" src="https://github.com/user-attachments/assets/572647fb-979d-48eb-8007-8460d52d242d" />

🔗 **Relationship 5: ServiceRequests → Employees**

1. In ServiceRequests table, find RequestedBy
2. Drag it to EmployeeID in the Employees table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

*Screenshot showing ServiceRequests and Employees tables -*

<img width="232" height="595" alt="image" src="https://github.com/user-attachments/assets/4a1bf0d3-cd1e-43e0-a9c6-ac5cc8a0924a" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="674" height="756" alt="image" src="https://github.com/user-attachments/assets/b8c8432e-9d08-4dbc-b585-8e6c276184a5" />

*Screenshot showing the relation created between ServiceRequests and Employees -

<img width="872" height="712" alt="image" src="https://github.com/user-attachments/assets/5726439f-435c-4540-b970-38362e7a1caf" />

🔗 **Relationship 6: Offers → Providers**

1. In Offers table, find ProviderID
2. Drag it to ProviderID in the Providers table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

*Screenshot showing Offers and Providers tables -*

<img width="493" height="240" alt="image" src="https://github.com/user-attachments/assets/c82d91ab-7135-4b1b-975a-dde72343bb50" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="519" height="839" alt="image" src="https://github.com/user-attachments/assets/dbdadfac-153b-41d9-b9e9-15cd36bd14b2" />

*Screenshot showing the relation created between Offers and Providers -

<img width="583" height="232" alt="image" src="https://github.com/user-attachments/assets/798c4e7a-150f-410e-a3dd-23a8df6069f4" />

🔗 **Relationship 7: Offers → ServiceRequests**

1. In Offers table, find RequestID
2. Drag it to RequestID in the ServiceRequests table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

*Screenshot showing ServiceRequests and Offers tables -*

<img width="512" height="271" alt="image" src="https://github.com/user-attachments/assets/842c92d4-0d51-40d9-93fd-e735b2d74040" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="678" height="756" alt="image" src="https://github.com/user-attachments/assets/f87120d7-8938-471c-885f-2e9657e37f97" />

*Screenshot showing the relation created between ServiceRequests and Offers -

<img width="586" height="273" alt="image" src="https://github.com/user-attachments/assets/4da219de-de02-41a4-9c94-e1d20eb73120" />

🔗 **Relationship 8: Skills → Employees**

1. In Skills table, find EmployeeID
2. Drag it to EmployeeID in the Employees table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

*Screenshot showing Employees and Skills tables -*

<img width="519" height="301" alt="image" src="https://github.com/user-attachments/assets/08cf4edc-8762-4cf2-9d2e-4dbbf7eb39b4" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="678" height="759" alt="image" src="https://github.com/user-attachments/assets/c7de0090-c8fe-4410-963f-44740e52f3a6" />

*Screenshot showing the relation created between Employees and Skills -

<img width="604" height="297" alt="image" src="https://github.com/user-attachments/assets/a6f113f1-5fc3-4a53-848d-f9eb11d3546a" />

🔗 **Relationship 9: ContractRoles → Contracts**

1. In ContractRoles table, find ContractID
2. Drag it to ContractID in the Contracts table
3. Settings:

      * Cardinality: "Many to one (*:1)"

4. Click OK

*Screenshot showing ContractRoles and Contracts tables -*

<img width="466" height="264" alt="image" src="https://github.com/user-attachments/assets/a01853dd-f34d-4782-b589-ed185a0a1ba3" />

*Screenshot showing the "Create relationship" window on Power BI -*

<img width="674" height="756" alt="image" src="https://github.com/user-attachments/assets/02c49708-eca0-4dfe-9a50-1ba6db698810" />

*Screenshot showing the relation created between ContractRoles and Contracts -

<img width="552" height="266" alt="image" src="https://github.com/user-attachments/assets/16f67660-38a3-4b24-bfb1-e95c14a1b582" />

---
### Relationships

*Screenshot displaying the complete set of relationships established among all tables -*

<img width="1914" height="1028" alt="image" src="https://github.com/user-attachments/assets/b2fe4ee6-b4ff-4fe9-b949-37e8266e93ba" />

---

### Create a Date Table (Calendar)

This is a special table for time-based analysis.

1. Look at the top ribbon and click the "Modeling" tab
2. Click the button "New table" (it has a table icon)
3. A formula bar appears at the top - delete anything in it
4. Type exactly this:

      **DimDate = CALENDAR(DATE(2023,1,1), DATE(2026,12,31))**

5. Press Enter on the keyboard
6. A new table called DimDate appears in the model!

*Screenshot displaying the new table DimDate in the model -*

<img width="1915" height="1027" alt="image" src="https://github.com/user-attachments/assets/672bdc8e-2af4-4fb0-b863-59599197d8c4" />

**Add more columns to Date table:**

1. Make sure DimDate is still selected
2. Click "New column" in the Modeling tab
3. Type:

      **Year = YEAR(DimDate[Date])**

4. Press Enter

*Screenshot displaying the new added column -*

<img width="1916" height="1027" alt="image" src="https://github.com/user-attachments/assets/aad68df8-9db0-4bd2-8131-2ebafba82786" />

5. Click "New column" again and type:

      **Month = FORMAT(DimDate[Date], "MMMM")**

6. Press Enter

*Screenshot displaying the new added column -*

<img width="1918" height="1029" alt="image" src="https://github.com/user-attachments/assets/67c7c3b1-ee63-44f1-bd24-b183bbcbc869" />

7. Click "New column" again and type:

      **MonthNum = MONTH(DimDate[Date])**

8. Press Enter

*Screenshot displaying the new added column -*

<img width="1916" height="1028" alt="image" src="https://github.com/user-attachments/assets/22a8c96b-ded2-449f-b483-4c6226e35b4a" />

---
### **CREATE DAX MEASURES:**
---
**What are measures?**

Measures are calculations that appear in the visuals (like totals, averages, counts).

**Create First Measure :**

1. On the right side of the screen, you'll see the "Data" panel listing all tables.
2. Right-click on any table (e.g., Employees)
3. Select "New measure"
4. A formula bar appears - type:

      **Total Employees = COUNTROWS(Employees)**

5. Press Enter

**Repeat to create all these measures:**

**Click New measure and type each one:**

```dax
Active Assignments = 
CALCULATE(
    COUNTROWS(Assignments),
    Assignments[AssignmentStatus] = "Active"
)
```
```dax
Open Service Requests = 
CALCULATE(
    COUNTROWS(ServiceRequests),
    ServiceRequests[Status] = "Open"
)
```
```dax
Submitted Offers = 
CALCULATE(
    COUNTROWS(Offers),
    Offers[OfferStatus] = "Submitted"
)
```

