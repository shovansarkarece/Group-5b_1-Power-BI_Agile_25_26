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

### Challenges & Solutions

**Challenge:** Import wizard showed data type errors for decimal columns.  
**Solution:** Manually set Price and Profit to DECIMAL(10,2) in Edit Mappings.

**Challenge:** Date column imported as text.  
**Solution:** Changed data type from DT_WSTR to DT_DATE in column configuration.

**Challenge:** Couldn't find Import Wizard option.  
**Solution:** Had to right-click on the database (not server) to access Tasks → Import Data.

### Key Learnings
- SQL Server Express is free and suitable for development
- Import Wizard provides easy GUI-based data import
- Always verify row counts and data integrity after import
- Primary keys and indexes improve query performance
- DECIMAL type should be used for financial data (not FLOAT)

### Application in Project
This SQL Server database will:
- Serve as the data source for Power BI reports
- Enable SQL-based analysis and querying
- Support multiple users accessing the same data
- Provide better performance than flat files

---
