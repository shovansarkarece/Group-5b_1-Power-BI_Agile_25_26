## Dataset Imported Successfully into SQL Server

### Objective
To import the cleaned and transformed dataset from Power Query into SQL Server, creating a centralized database that can serve as a reliable data source for Power BI and enable SQL-based querying and analysis.

### Business Context
Storing data in SQL Server provides several advantages:
- **Centralized Data Repository:** Single source of truth for organizational data
- **Multi-User Access:** Multiple users and applications can access the same data
- **Data Security:** Built-in authentication, authorization, and encryption
- **Performance:** Optimized for large datasets and complex queries
- **Scalability:** Can handle growing data volumes efficiently
- **Integration:** Seamless connection with Power BI and other Microsoft tools
- **Data Governance:** Better control over data quality and compliance

SQL Server acts as the foundation for enterprise reporting and analytics solutions.

### Prerequisites

**Software Requirements:**
1. **SQL Server** (I used SQL Server 2022 Express Edition - Free)
2. **SQL Server Management Studio (SSMS)** - Version 19.3
3. **Cleaned dataset** from Power Query (exported to CSV/Excel)

**System Information:**
- Operating System: Windows 11
- SQL Server Version: SQL Server 2022 Express (16.0.1000.6)
- SQL Server Instance: `localhost\SQLEXPRESS`
- Authentication Mode: Windows Authentication

### Steps Performed

#### Phase 1: SQL Server Installation and Setup

1. **Downloaded SQL Server Express**
   - Visited Microsoft's official download page
   - Downloaded SQL Server 2022 Express Edition (free version)
   - File size: ~270 MB

2. **Installed SQL Server**
   - Ran the installer
   - Selected **Basic Installation** option
   - Accepted default settings
   - Installation completed successfully
   - Instance name: `SQLEXPRESS`

3. **Installed SQL Server Management Studio (SSMS)**
   - Downloaded SSMS 19.3 from Microsoft
   - Installed with default settings
   - Launched SSMS and connected to local instance






