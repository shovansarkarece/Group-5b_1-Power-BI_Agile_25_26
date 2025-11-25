## Dataset Imported Successfully into SQL Server

### Objective
Import the cleaned dataset from Power Query into SQL Server to create a centralized database for Power BI reporting.

### Business Context
SQL Server provides:
- Centralized data storage
- Multi-user access
- Better performance for large datasets
- Seamless Power BI integration
- Enhanced security and data governance

### Prerequisites
- SQL Server 2022 Express Edition (Free)
- SQL Server Management Studio (SSMS) 19.3
- Cleaned dataset exported from Power Query

### Steps Performed

#### 1. SQL Server Installation
- Downloaded and installed SQL Server 2022 Express
- Installed SQL Server Management Studio (SSMS)
- Verified SQL Server service is running
- Instance name: `localhost\SQLEXPRESS`

#### 2. Database Creation
- Create database
- Verify creation

#### 3. Export Data from Power Query
- In Power BI Desktop, closed and applied Power Query transformations
- Exported cleaned data to CSV: `Sales_Data_Cleaned.csv`
- Verified: 9995 rows, 21 columns

#### 4. Import Data Using Import Wizard
- In SSMS, right-clicked database → **Tasks** → **Import Data**
- **Data Source:** Flat File Source → Selected CSV file
- **Destination:** SQL Server Native Client → `PowerBI_Sales_DB`
- **Table:** Created new table `dbo.Sales_Data`
- Configured column mappings:

| Column | Data Type | Size |
|--------|-----------|------|
| Order ID | int | - |
| Order Date | date | - |
| Customer Name | nvarchar | 100 |
| Product | nvarchar | 100 |
| Category | nvarchar | 50 |
| Quantity | int | - |
| Price | decimal | 10,2 |
| Profit | decimal | 10,2 |

- Executed import → **Success: 9995 rows transferred**

### Results
- ✅ Database created: PowerBI_Sales_DB
- ✅ Table created: dbo.Sales_Data
- ✅ Rows imported: 9995 (100% success)


