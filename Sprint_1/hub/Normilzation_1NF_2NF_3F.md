# 📘 Normalization 

---

# ⭐ What is Normalization? (Simple Definition)

Normalization is a method to clean our data table so that:

- No duplicate data

- No confusing / mixed data

- Easy to maintain

- No update problems

---

# 🟢 1NF — First Normal Form  
### ✅ Rules  
- No multiple values in one column  
- No repeating groups  
- Every cell must contain a **single (atomic) value**

### ❌ Bad Example (Not in 1NF)
| Student | PhoneNumbers       |
|--------|---------------------|
| Ram    | 12345, 98765        |
| Sita   | 55555, 66666, 77777 |

### ✔ Correct 1NF Table
| Student | PhoneNumber |
|---------|-------------|
| Ram     | 12345       |
| Ram     | 98765       |
| Sita    | 55555       |
| Sita    | 66666       |
| Sita    | 77777       |

---

## 🧩 **1NF Diagram (Mermaid)**

```mermaid
erDiagram
    STUDENT {
        string Student
        string PhoneNumber
    }
````

---

# 🟡 2NF — Second Normal Form

### Applies only when:

✔ Table has **composite primary key**
✔ No **partial dependency**

### ❌ Bad Table (Not in 2NF)

Composite Key = OrderID + ProductID

| OrderID | ProductID | ProductName | Quantity |
| ------- | --------- | ----------- | -------- |
| 1       | 101       | Pen         | 2        |
| 1       | 102       | Pencil      | 5        |

❌ Problem:

* ProductName depends only on ProductID (partial dependency)

---

### ✔ Correct 2NF (Split Tables)

**OrderDetails Table**

| OrderID | ProductID | Quantity |
| ------- | --------- | -------- |

**Products Table**
| ProductID | ProductName |

---

## 🧩 **2NF Diagram (Mermaid)**

```mermaid
erDiagram
    ORDERDETAILS {
        int OrderID
        int ProductID
        int Quantity
    }
    PRODUCTS {
        int ProductID
        string ProductName
    }
    ORDERDETAILS }o--|| PRODUCTS : "ProductID"
```

---

# 🔵 3NF — Third Normal Form

### 🚫 No Transitive Dependency

Non-key columns must NOT depend on other non-key columns.

---

### ❌ Bad Example (Not in 3NF)

| EmployeeID | EmployeeName | DepartmentID | DepartmentName |
| ---------- | ------------ | ------------ | -------------- |

❌ Problem:
DepartmentName depends on DepartmentID (not primary key)

---

### ✔ Correct 3NF Structure

**Employees Table**
| EmployeeID | EmployeeName | DepartmentID |

**Departments Table**
| DepartmentID | DepartmentName |

---

## 🧩 **3NF Diagram (Mermaid)**

```mermaid
erDiagram
    EMPLOYEES {
        int EmployeeID
        string EmployeeName
        int DepartmentID
    }
    DEPARTMENTS {
        int DepartmentID
        string DepartmentName
    }
    EMPLOYEES }o--|| DEPARTMENTS : "DepartmentID"
```

---

# 🟣 Putting It All Together (Full Example)

### Starting Table (Bad)

| OrderID | CustomerName | Product | ProductPrice | Qty |
| ------- | ------------ | ------- | ------------ | --- |
| 1       | Ram          | Pen     | 10           | 2   |
| 1       | Ram          | Pencil  | 5            | 3   |

---

## ✔ 1NF → Already atomic

No multivalues.

---

## ✔ 2NF → Split customer & product

**Orders**

| OrderID | CustomerName |
| ------- | ------------ |

**OrderDetails**
| OrderID | Product | Qty |

**Products**
| Product | ProductPrice |

---

## ✔ 3NF → Remove transitive dependencies

**Customers Table**
| CustomerID | CustomerName |

**Products Table**
| ProductID | ProductName | ProductPrice |

**Orders Table**
| OrderID | CustomerID |

**OrderDetails Table**
| OrderID | ProductID | Qty |

---

## 🧩 **Complete ER Diagram**

```mermaid
erDiagram
    CUSTOMERS {
        int CustomerID
        string CustomerName
    }
    PRODUCTS {
        int ProductID
        string ProductName
        float Price
    }
    ORDERS {
        int OrderID
        int CustomerID
    }
    ORDERDETAILS {
        int OrderID
        int ProductID
        int Quantity
    }

    ORDERS }o--|| CUSTOMERS : "CustomerID"
    ORDERDETAILS }o--|| ORDERS : "OrderID"
    ORDERDETAILS }o--|| PRODUCTS : "ProductID"
```

---

# 🟢 Normalization Summary Table

| Normal Form | Simple Meaning           | Fix                  |
| ----------- | ------------------------ | -------------------- |
| **1NF**     | No multiple values       | Split rows           |
| **2NF**     | No partial dependency    | Split tables         |
| **3NF**     | No transitive dependency | Create lookup tables |

---

# 📌 Where This Helps in Power BI

* Removes duplicate values
* Reduces data size
* Fixes many-to-many issues
* Improves relationship modeling
* Enables star schema (fact + dimension)

---


