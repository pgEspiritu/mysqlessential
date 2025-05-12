# 🛠️ Database Design and Storage in MySQL

In this module, we will cover the fundamentals of database design in MySQL. By the end of this module, you will be able to:

- Understand how MySQL stores data on the file system
- Create databases and tables for data storage
- Implement indexes to improve query performance
- Join tables in your queries
- Utilize partitioning to manage data storage across different locations

---

## 📦 Data Storage in MySQL

### Storage Engine Layer
MySQL's storage engine layer is part of the server process. It functions between the server components responsible for:

- Inputting, parsing, and optimizing SQL
- Interacting with the underlying file systems

### InnoDB - The Default Storage Engine
- **InnoDB** is the default storage engine for MySQL.
- It provides features necessary for production database systems, including:
  - Transaction support
  - Referential integrity
  - ACID compliance
  - Data encryption and compression

### Other Storage Engines
- **MyISAM**: Fast and basic, but lacks reliability features.
- **NDB Cluster**: Scalable and distributed across multiple nodes.

---

## ✅ InnoDB Features and Benefits

- **Concurrent User Support:** Keeps changes separate for multiple users.
- **Transactions:** Changes can be rolled back if necessary.
- **Referential Integrity:** Ensures dependent data is valid.
- **Data Storage Structure:** Data is stored in a B-tree structure to optimize query performance.
- **Index Storage:** Similar structure to data storage, allowing for quick retrieval.
- **Buffer Pool:** Caches frequently accessed data for faster querying.
- **Performance Optimizations:** Multithreading and bulk insert optimization.

---

## 🔥 Understanding ACID Properties

- **Atomicity:** A transaction is treated as a single operation that either fully succeeds or fully fails.
- **Consistency:** Ensures that data moves from one consistent state to another.
- **Isolation:** Changes made during a transaction are invisible to other users until committed.
- **Durability:** Once a transaction is committed, it is persisted to disk.

---

## 📝 Transactions in MySQL

InnoDB supports transaction syntax, such as:

- `START TRANSACTION` or `BEGIN`: Begins a transaction.
- `COMMIT`: Saves changes made in a transaction.
- `ROLLBACK`: Discards changes made in a transaction.

> **Note:** Data Definition Language (DDL) statements, such as `CREATE TABLE`, trigger an implicit commit.

### Example:

```sql
START TRANSACTION;

INSERT INTO orders (customer_id, order_date) VALUES (1, '2025-05-12');
INSERT INTO orders (customer_id, order_date) VALUES (2, '2025-05-12');

-- Rollback the transaction
ROLLBACK;

-- Only this INSERT will persist as it is executed after ROLLBACK
INSERT INTO orders (customer_id, order_date) VALUES (3, '2025-05-12');

```

## 🚀 Autocommit Mode  

- **Enabled by Default:** Each DML statement (`INSERT`, `UPDATE`, `DELETE`) is committed automatically.  

### To Control Transaction Behavior:  
- Use `START TRANSACTION` or `BEGIN` to temporarily disable autocommit.  
- Manually use `COMMIT` or `ROLLBACK` as needed.  

---

## 🔍 Indexing and Data Retrieval  

- **InnoDB** uses **B-tree structures** to organize data.  
- Indexes are stored similarly to data, allowing for quick access and retrieval.  
- Use indexes to optimize query performance and reduce response time.  

---

## 🗄️ Data Partitioning  

Partitioning allows data to be divided into smaller, more manageable parts:  

- Improves performance for large datasets.  
- Enables distribution of data across different locations.  
- Can be configured based on `range`, `list`, `hash`, or `key` values.  

---

## 📚 Additional Resources  

- [MySQL InnoDB Documentation](https://dev.mysql.com/doc/refman/8.0/en/innodb-storage-engine.html)  
- [MySQL Partitioning](https://dev.mysql.com/doc/refman/8.0/en/partitioning.html)  
- [MySQL Transactions](https://dev.mysql.com/doc/refman/8.0/en/commit.html)  
