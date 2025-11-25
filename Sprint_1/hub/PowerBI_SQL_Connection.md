## SQL Server Connected to Power BI Desktop

### Objective
Establish a connection between Power BI Desktop and SQL Server database to enable data visualization and reporting.

### Business Context
Connecting Power BI to SQL Server enables:
- Real-time data access from centralized database
- Better performance for large datasets
- Shared data source for multiple reports
- Automatic refresh capabilities
- Enterprise-grade security

### Steps Performed

#### 1. Opened Power BI Desktop
- Launched Power BI Desktop application
- Created new blank report

#### 2. Connected to SQL Server
- Clicked **Get Data** → **SQL Server**
- Entered connection details:
  - **Server:** `localhost\SQLEXPRESS`
  - **Database:** `PowerBI_Sales_DB`
- Selected **Import** mode (DirectQuery also available)
- Clicked **OK**

#### 3. Selected Tables
- Navigator window opened showing available tables
- Selected `dbo.Sales_Data` table
- Previewed data to verify (9,995 rows visible)
- Clicked **Load**

#### 4. Verified Data Load
- Checked **Fields** pane on right side
- Confirmed `Sales_Data` table with all 21 columns:
- Verified row count: 9995 rows loaded successfully

#### 5. Tested Connection
- Created a simple table visual to test
- Dragged `Category` and `Sales_Amount` fields
- Data displayed correctly
- Connection working ✅

### Connection Details

**Server:** localhost\SQLEXPRESS  
**Database:** PowerBI_Sales_DB  
**Table:** dbo.Sales_Data  
**Connection Type:** Import  
**Authentication:** Windows Authentication  
**Rows Loaded:** 9,995  
**Columns Loaded:** 21  

### Import vs DirectQuery

**Import Mode** (Used in this project):
- Data loaded into Power BI memory
- Faster performance for visualizations
- Requires refresh to get updated data
- Best for: Small to medium datasets

**DirectQuery Mode:**
- Queries SQL Server in real-time
- Always shows current data
- Slower performance (depends on SQL Server)
- Best for: Large datasets, real-time requirements

### Results
- ✅ Successfully connected to SQL Server
- ✅ Loaded 9,995 rows from Sales_Data table
- ✅ All 21 columns imported correctly
- ✅ Data types preserved from SQL Server
- ✅ Test visualization created successfully
- ✅ Connection stable and working

