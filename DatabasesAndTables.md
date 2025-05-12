# 🛠️ Database Design in MySQL  

In this section, we cover the essential features of MySQL database design, including schemas, tables, data types, and storage options.

---

## 📦 Schema vs. Database  
- **Schema** and **Database** are synonymous in MySQL.  
- Each database is a directory in the file system, typically within the `data` directory.  
- Tables store row data in files, with **InnoDB** using the InnoDB tablespace by default.  

---

## 🛠️ System-Level Databases  
- **MySQL** and **Information Schema:** Store authentication settings and table metadata.  
- **Performance Schema & Sys:** Provide performance metrics and system information.  
- **InnoDB Cluster Metadata:** Configurations for highly available clusters.  

---

## 📝 Creating a Table  

General Syntax:  

```sql
CREATE TABLE schema_name.table_name (
    id INT NOT NULL AUTO_INCREMENT,
    lastname VARCHAR(45) NOT NULL,
    forename VARCHAR(45) NOT NULL,
    birthday DATE NOT NULL,
    PRIMARY KEY (id)
);

```

# 🛠️ Column Definitions in MySQL  

## ✅ Column Options  
- **AUTO_INCREMENT:** Automatically increments the `id` column.  
- **NOT NULL:** Ensures that the column cannot store `NULL` values.  

---

## 🧮 Data Types Overview  

### 🧾 Numeric Data Types  
- **INT:** 4 bytes, ±2 billion range.  
- **TINYINT:** 1 byte, range -128 to 127.  
- **SMALLINT:** 2 bytes, range -32,768 to 32,767.  
- **FLOAT / DOUBLE:** Approximate decimal numbers (not for precise calculations).  
- **BIT:** Stores `0` or `1` values.  

---

### 📅 Date and Time Data Types  
- **DATE:** Stores `YYYY-MM-DD`.  
- **TIME:** Stores `HH:MM:SS`.  
- **DATETIME:** Combines both date and time.  

---

### 📝 String Data Types  
- **CHAR(n):** Fixed-width string, always takes `n` characters.  
- **VARCHAR(n):** Variable-width string, up to `n` characters.  
- **BINARY / VARBINARY:** Store byte sequences.  
- **ENUM:** A predefined list of strings, stored as numeric indexes.  
- **SET:** A collection of strings, allowing multiple values.  

---

### 🗄️ Special Data Types  
- **BLOB / TINYBLOB / LONGBLOB:** Binary data, such as images or audio files.  
- **TEXT / TINYTEXT / LONGTEXT:** Large text data.  
- **JSON:** Allows storage of JSON documents with query capabilities.  
- **SPATIAL:** Represents geographic data like points, lines, and polygons.  

---

## 🔗 Additional Resources  
- [MySQL Data Types Documentation](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)  
- [Creating Tables in MySQL](https://dev.mysql.com/doc/refman/8.0/en/creating-tables.html)  
- [MySQL Storage Engines](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)  

