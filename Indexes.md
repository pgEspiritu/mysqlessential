# 🚀 Optimizing Query Performance with Indexes  

Indexes make it easier for MySQL to find specific rows, speeding up queries and ensuring that new rows are inserted in optimal positions for future queries.

---

## 🛠️ How Indexes Work  
- Indexes store raw data or subsets of data in a defined order.  
- Indexes can be ordered on non-unique values (e.g., `name`) or unique values (e.g., `ID`).  
- **Primary Index (Clustered Index):** The complete table data ordered by a unique value (Primary Key).  

---

## 📦 Types of Indexes in InnoDB  

- **BTREE:** Most secondary indexes use a B-tree structure.  
- **HASH:** Supported by some storage engines like MEMORY; InnoDB has an adaptive HASH feature.  
- **RTREE:** Used for spatial data indexing.  

---

## ✅ Best Practices for Indexes  

1. **Create a Primary Key:**  
   - Ensures uniqueness for each row.  
   - InnoDB automatically creates a hidden Primary Key if not explicitly defined.  

2. **Minimize Indexes:**  
   - Too many indexes slow down `INSERT`, `UPDATE`, and `DELETE` operations.  
   - Only create indexes that are necessary for query optimization.  

3. **Use Prefix Keys:**  
   - Index only the first part of a string to reduce index size.  

4. **Compound Keys:**  
   - Combine multiple columns in an index to speed up multi-column queries.  

5. **Monitor Index Usage:**  
   - Use the **sys schema** in MySQL Enterprise Monitor to identify unused indexes.  

---

## 📦 Example Table and Index Definition  

```sql
CREATE TABLE customers (
    id INT UNSIGNED PRIMARY KEY,
    email VARCHAR(100),
    lname CHAR(30),
    fname CHAR(30),
    INDEX idx_name (lname, fname)
);

```

## Example Queries

### Select by Last Name:
```sql
SELECT * FROM customers WHERE lname = 'Smith';

Uses the compound index on lname, fname.

Select by Last and First Name:

SELECT * FROM customers WHERE lname = 'Smith' AND fname = 'John';

Uses both lname and fname in the compound index.
```
