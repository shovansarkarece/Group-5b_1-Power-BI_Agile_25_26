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


