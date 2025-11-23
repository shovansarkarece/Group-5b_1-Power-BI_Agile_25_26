# Fact and Dimensions of Table Concepts in Data Modeling

Here you can find about the table concepts in detail.

### **INTRODUCTION TO DATABASE TABLES**

A table is a structured collection of data organized in rows and columns within a database. It represents a single entity or subject (like customers, products, or orders) and is the fundamental building block of relational databases.

**Structure:**

- Rows (Records/Tuples): Horizontal entries representing individual instances of the entity
- Columns (Fields/Attributes): Vertical divisions representing specific characteristics of the entity
- Cells: Intersection of rows and columns containing individual data values

Example:

| CustomerID | CustomerName | City    | Country |
|------------|--------------|---------|---------|
| 1          |          A   | Berlin  | Germany      |
| 2          |            B | Frankfurt  | Germany   |
| 3          |      C       | London | UK   |


### **TYPES OF TABLES IN DATA MODELING**

**1. Fact Tables:** 

Fact tables store quantitative, measurable data about business processes and transactions. They contain the metrics that organizations want to analyze.

<ins>Characteristics:</ins>

- Large volume: Contains millions to billions of rows
- Numeric data: Primarily stores measurements and metrics
- Foreign keys: Contains multiple foreign keys referencing dimension tables
- Grain: Defines the level of detail (e.g., per transaction, per day, per customer)
- Additive measures: Values that can be summed across dimensions
- Rapidly growing: New records added continuously

<ins>Components:</ins>

Measures (Facts):
- Quantitative values for analysis
- Examples: Sales Amount, Quantity Sold, Profit, Cost, Duration, Count
- Types:
  - Additive: Can be summed across all dimensions (e.g., Sales Amount)
  - Semi-additive: Can be summed across some dimensions (e.g., Account Balance - not across time)
  - Non-additive: Cannot be summed (e.g., Ratios, Percentages, Unit Price)

Foreign Keys:
- Reference primary keys in dimension tables
- Create relationships between fact and dimension tables
- Examples: CustomerID, ProductID, DateID, StoreID

Degenerate Dimensions:

- Dimension keys stored in fact table without corresponding dimension table
- Examples: Invoice Number, Order Number, Transaction ID

Types of Fact Tables:

1. Transaction Fact Table:

- Records individual business transactions
- Most granular level of detail
- Example: Each sale, each website click, each phone call

2. Periodic Snapshot Fact Table:

- Records data at regular intervals
- Shows status at specific points in time
- Example: Daily inventory levels, monthly account balances

3. Accumulating Snapshot Fact Table:

- Tracks processes with defined beginning and end
- Records multiple milestone dates
- Example: Order fulfillment (order date, ship date, delivery date)

4. Factless Fact Table:

- Records events without numeric measures
- Tracks occurrences or relationships
- Example: Student course enrollment, employee shift attendance

**2. Dimension Tables**

Dimension tables contain descriptive, textual attributes that provide context to the measures in fact tables. They answer "who, what, where, when, why, and how" questions about the data.

<ins>Characteristics:</ins>

- Smaller volume: Fewer rows compared to fact tables (hundreds to thousands)
- Wide tables: Many columns (attributes) describing the entity
- Descriptive data: Text, dates, and categorical information
- Primary key: Unique identifier (often surrogate key)
- Slowly changing: Updated infrequently
- Denormalized: Often contains redundant data for query performance

<ins>Components:</ins>

Primary Key:
- Unique identifier for each row
- Types:
  - Natural Key: Business meaningful (e.g., ProductSKU, EmployeeSSN)
  - Surrogate Key: System-generated integer (e.g., ProductID, CustomerID)

Attributes:
- Descriptive fields providing context
- Examples: Product Name, Customer Address, Category Name, Store Location

Hierarchies:
- Natural groupings within dimension
- Examples:
  - Date: Day → Month → Quarter → Year
  - Geography: City → State → Region → Country
  - Product: Product → Subcategory → Category → Department

Types of Dimension Tables:

1. Conformed Dimensions:
- Shared across multiple fact tables
- Ensures consistent analysis
- Example: Date dimension used in Sales, Inventory, and HR fact tables

2. Role-Playing Dimensions:
- Same dimension used multiple times with different meanings
- Example: Date dimension as Order Date, Ship Date, Delivery Date

3. Junk Dimensions:
- Combines low-cardinality flags and indicators
- Reduces fact table width
- Example: Payment Method, Order Status, Shipping Type combined

4. Degenerate Dimensions:
- Dimension attribute stored in fact table
- No separate dimension table
- Example: Invoice Number, Transaction ID

**3. Bridge Tables (Junction/Linking Tables)**

Bridge tables resolve many-to-many relationships between two tables by creating two one-to-many relationships.

<ins>Purpose:</ins>

- Handle complex relationships that cannot be directly modeled
- Enable proper data normalization
- Maintain referential integrity

Example Scenario:

Students can enroll in multiple courses, and courses can have multiple students enrolled.

<ins>Structure:</ins>

Students Table

| StudentID | StudentName   |
|-----------|---------------|
| 1         | AAA |
| 2         | BBB |

Courses Table

| CourseID | CourseName       |
|----------|------------------|
| 101      | Data Science     |
| 102      | Machine Learning |

<ins>Bridge Table:</ins> Student_Course_Enrollment

| EnrollmentID | StudentID | CourseID | EnrollmentDate | Grade |
|--------------|-----------|----------|----------------|-------|
| 1            | 1         | 101      | 2024-01-15     | A     |
| 2            | 1         | 102      | 2024-01-15     | B+    |
| 3            | 2         | 101      | 2024-01-16     | A-    |

Common Use Cases:
- Product-Supplier relationships (products from multiple suppliers)
- Employee-Project assignments (employees on multiple projects)
- Customer-Product ownership (customers owning multiple products)

**4. Lookup Tables (Reference Tables)**

Lookup tables store static, reference data used for validation, categorization, or standardization across the database.

<ins>Characteristics:</ins>

- Small, rarely changing
- Contains code-description pairs
- Used for data validation
- Improves data consistency

Examples:

Country_Lookup

| CountryCode | CountryName     | Continent   |
|-------------|-----------------|-------------|
| US          | United States   | N. America  |
| UK          | United Kingdom  | Europe      |
| CN          | China           | Asia        |

Status_Lookup

| StatusID | StatusName   |
|----------|--------------|
| 1        | Pending      |
| 2        | In Progress  |
| 3        | Completed    |
| 4        | Cancelled    |

### **TABLE RELATIONSHIPS AND CARDINALITY**
1. **One-to-Many (1:M) Relationship**

One record in Table A can be associated with multiple records in Table B, but each record in Table B is associated with only one record in Table A.
Most Common Relationship Type - Used in approximately 80-90% of database relationships.

Implementation:
- Primary key in the "one" side table
- Foreign key in the "many" side table

**Real-World Examples:**

Customer to Orders:
- One customer can place many orders
- Each order belongs to one customer

Department to Employees:
- One department has many employees
- Each employee belongs to one department

Category to Products:
- One category contains many products
- Each product belongs to one category

Database Diagram:

Customers Table

| CustomerID (PK) | Name           | Email              |
|-----------------|----------------|--------------------|
| 1               | AAAA  | XXXXXXX    |
| 2               | BBBB   | XXXXXXXX     |

Orders Table

| OrderID (PK) | OrderDate  | CustomerID (FK) | Amount |
|--------------|------------|-----------------|--------|
| 101          | 2024-01-15 | 1               | 250.00 |
| 102          | 2024-01-16 | 1               | 125.00 |
| 103          | 2024-01-17 | 2               | 300.00 |

2. **Many-to-One (M:1) Relationship**

The reverse perspective of one-to-many. Multiple records in Table A relate to one record in Table B.

Note: This is functionally identical to one-to-many, just viewed from the opposite direction.

3. **One-to-One (1:1) Relationship**

One record in Table A relates to exactly one record in Table B, and vice versa.

**Usage Scenarios:**

Security/Privacy:

Separate sensitive data (e.g., Employee basic info vs. Salary details)

Performance:

Split large tables with many columns

Optional Information:

Not all records need the related information

Employee Table

| EmployeeID (PK) | Name           | Department |
|-----------------|----------------|------------|
| 1               | AAAA  | HR         |
| 2               | BBBB   | IT         |

Employee_Salary Table

| EmployeeID (PK, FK) | Salary  | BonusRate |
|---------------------|---------|-----------|
| 1                   | 60000   | 10%       |
| 2                   | 75000   | 12%       |

Person Table
| PersonID (PK) | Name           | DOB        |
|---------------|----------------|------------|
| 1             | CCCC  | 1990-05-12 |
| 2             | DDDD      | 1985-09-23 |

Passport Table
| PassportNo (PK) | PersonID (FK) | IssueDate  |
|-----------------|---------------|------------|
| X12345          | 1             | 2020-01-15 |
| Y67890          | 2             | 2021-03-20 |

4. **Many-to-Many (M:N) Relationship**

Multiple records in Table A can relate to multiple records in Table B, and vice versa.

Problem: 

Cannot be directly implemented in relational databases without creating data redundancy or anomalies.

Solution:

Create a bridge table (junction table) that breaks the many-to-many into two one-to-many relationships.

<ins>Structure:</ins>

Students
| StudentID (PK) | Name           | Email              |
|----------------|----------------|--------------------|
| 1              | AAAA  | xxxxxxx   |
| 2              | BBBB   | xxxxxxx     |

Enrollment
| EnrollmentID (PK) | StudentID (FK) | CourseID (FK) | Grade | Semester |
|-------------------|----------------|---------------|-------|----------|
| 1                 | 1              | 101           | A     | Fall 2024|
| 2                 | 1              | 102           | B+    | Fall 2024|
| 3                 | 2              | 101           | A-    | Fall 2024|

Courses
| CourseID (PK) | CourseName       | Credits |
|---------------|------------------|---------|
| 101           | Agile Development     | 3       |
| 102           | Machine Learning | 4       |

Other Common M:N Examples:

Products and Suppliers:

- Products from multiple suppliers
- Suppliers provide multiple products
- Bridge: Product_Supplier table

Actors and Movies:

- Actors in multiple movies
- Movies with multiple actors
- Bridge: Cast table

Authors and Books:

- Authors write multiple books
- Books can have multiple authors
- Bridge: Book_Author table

**4. TABLE KEYS**

**Primary Key (PK):**

A column (or combination of columns) that uniquely identifies each row in a table.

Rules:

- Must contain unique values
- Cannot contain NULL values
- Each table should have only one primary key
- Should be immutable (not change over time)

**Foreign Key (FK):**

A column (or columns) that creates a link between two tables by referencing the primary key of another table.

Purpose:

- Enforce referential integrity
- Establish relationships between tables
- Prevent orphaned records

**Candidate Key:**

Any column (or combination) that could serve as a primary key. A table can have multiple candidate keys.

Example:

Employee Table

- EmployeeID (chosen as PK)
- Email (candidate key - unique)
- SSN (candidate key - unique)

**Alternate Key:**

Candidate keys that were NOT chosen as the primary key.

Example:

If EmployeeID is the primary key, then Email and SSN are alternate keys.


**Surrogate Key:**

An artificially created key (usually auto-incrementing integer) with no business meaning.

Advantages:

- Simple, compact (usually integer)
- Immutable
- No dependency on business logic
- Improves join performance


**Natural Key:**

A key based on actual data that has business meaning.

Examples:

- Social Security Number (SSN)
- ISBN for books
- Email address
- Product SKU

Disadvantages:

- Can change (email changes)
- May be long (composite keys)
- Privacy concerns
- Can impact performance

**Composite Key:**

A primary key consisting of two or more columns combined.

Example:

Order_Details Table

| OrderID (PK) | ProductID (PK) | Quantity | Price |
|--------------|----------------|----------|-------|
| 101          | P01            | 2        | 25.00 |
| 101          | P02            | 1        | 15.00 |
| 102          | P01            | 3        | 25.00 |

**5. TABLE NORMALIZATION**

Purpose of Normalization:

- Eliminate data redundancy
- Ensure data integrity
- Reduce update anomalies
- Organize data logically

**Normal Forms:**

1NF (First Normal Form):

- Each cell contains atomic (indivisible) values
- No repeating groups
- Each record is unique

Before 1NF

| CustomerID | PhoneNumbers           |
|------------|------------------------|
| 1          | 123-4567, 987-6543     |


After 1NF

| CustomerID | PhoneNumber |
|------------|-------------|
| 1          | 123-4567    |
| 1          | 987-6543    |

2NF (Second Normal Form):

Must be in 1NF
No partial dependencies (all non-key attributes depend on entire primary key)

3NF (Third Normal Form):

Must be in 2NF
No transitive dependencies (non-key attributes depend only on primary key)

BCNF (Boyce-Codd Normal Form):

Stricter version of 3NF
Every determinant is a candidate key

**6. DENORMALIZATION FOR DATA WAREHOUSING**

Purpose: 

In analytical databases (data warehouses), we often deliberately denormalize to:

- Improve query performance (fewer joins)
- Simplify queries for business users
- Optimize for read operations

Trade-offs:

Advantages:

- Faster queries
- Reduced complexity
- Better suited for BI tools

Disadvantages:

- Data redundancy
- Larger storage requirements
- More complex updates
- Potential data inconsistency

**7. BEST PRACTICES FOR TABLE DESIGN**

Naming Conventions

Use clear, descriptive names:

**Good:** Customer, Order_Details, Product_Category

**Bad:** Tbl1, Data, Temp

**Column Design:**

Choose appropriate data types:

- Use smallest type that fits
- INT for IDs, DECIMAL for money, DATE for dates

Allow NULL only when necessary:

- Use NOT NULL constraint for required fields
- Set default values where appropriate

Indexing:

- Always index primary keys (automatic in most databases)
- Index foreign keys for join performance
- Index frequently queried columns
- Don't over-index (impacts insert/update performance)

Documentation:

- Document table purpose
- Describe each column
- Explain relationships
- Note business rules

**8. SUMMARY COMPARISON TABLE**

AspectFact TableDimension TablePurposeStore measurementsStore descriptive contextSizeMillions-billions of rowsHundreds-thousands of rowsWidthNarrow (few columns)Wide (many columns)Data TypeNumeric, quantitativeText, categoricalKeysMultiple foreign keysSingle primary keyGrowthRapid, continuousSlow, occasionalQueriesAggregated (SUM, AVG)Filtered, grouped byExampleSales transactionsCustomer information

The above guide covers all essential table concepts.
