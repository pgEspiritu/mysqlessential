### 36. MULTIPLE CHOICE
**Which thread reads the relay log and executes the transactions that it contains on the replica?**

- [ ] Connection thread  
- [ ] I/O thread  
- [ ] I/O binlog dump thread  
- [x] SQL thread  

> **Explanation:** The replica creates a SQL thread to read the relay log that is written by the replication I/O thread and execute the transactions contained in it.

---

### 37. MULTIPLE CHOICE
**Which two are NOT used when setting up MySQL InnoDB ReplicaSet?**

- [x] MySQL Workbench  
- [ ] MySQL Router  
- [ ] MySQL Shell  
- [x] MySQL Group Replication  
- [ ] MySQL Read Replica  

> **Explanation:** MySQL Workbench and Group Replication are not used. MySQL Shell provides the AdminAPI to manage ReplicaSet; MySQL Router enables transparent routing.

---

### 38. MULTIPLE CHOICE
**Which MySQL component redirects application queries to available nodes in an InnoDB Cluster?**

- [ ] MySQL Workbench  
- [x] MySQL Router  
- [ ] MySQL Shell  
- [ ] MySQL Group Replication  

> **Explanation:** MySQL Router automatically connects client applications to server instances and reconfigures after failure.

---

### 39. MULTIPLE CHOICE
**Which MySQL component automates InnoDB Cluster creation and makes managing the Cluster easy?**

- [x] MySQL Shell  
- [ ] MySQL Group Replication  
- [ ] MySQL Router  
- [ ] MySQL Workbench  

> **Explanation:** MySQL Shell uses AdminAPI to deploy and manage InnoDB Cluster.

---

### 40. MULTIPLE CHOICE
**What is the Recovery Point Objective (RPO) or data loss tolerance within a region when using MySQL InnoDB Cluster?**

- [x] Zero  
- [ ] Seconds to minutes  
- [ ] Minutes  
- [ ] Minutes to hours  

> **Explanation:** InnoDB Cluster uses Group Replication and guarantees zero data loss within a region.

---

### 41. MULTIPLE CHOICE
**Which MySQL component provides automatic failover when using InnoDB Cluster?**

- [x] MySQL Group Replication  
- [ ] MySQL Shell  
- [ ] MySQL Router  
- [ ] MySQL Workbench  

---

### 42. MULTIPLE CHOICE
**What does the MySQL Performance Schema do?**

- [ ] It creates indexes for the SQL code.  
- [ ] It scales the MySQL database for better performance.  
- [ ] It compresses the database for better underlying hardware management.  
- [x] It provides statistics about your MySQL instance.  

> **Explanation:** The Performance Schema provides statistics of how MySQL executes at a low level and is not replicated.

---

### 43. MULTIPLE CHOICE
**Which MySQL schema has its own dedicated storage engine?**

- [x] Performance schema  
- [ ] mysql schema  
- [ ] world schema  
- [ ] sakila Schema  

> **Explanation:** Performance schema uses its own engine called `PERFORMANCE_SCHEMA`.

---

### 44. MULTIPLE CHOICE
**Which part of the database is the highest source of Database Performance Problems?**

- [ ] The underlying hardware  
- [ ] The database structure  
- [ ] The overall size of retained data in the active dataset  
- [x] The SQL, index, and Schema group  

---

### 45. MULTIPLE CHOICE
**What can you do with MySQL in Oracle Enterprise Manager?**

- [x] Back up a MySQL database instance.  
- [ ] Create a MySQL InnoDB ReplicaSet.  
- [ ] Add extra security to the MySQL database.  
- [x] Monitor MySQL Performance.  

> **Explanation:** Oracle Enterprise Manager monitors MySQL performance, availability, replication topology, and more.

---

### 46. MULTIPLE CHOICE
**Slow query log is used to capture long-running SQL statements.  
Which is NOT logged by default?**

- [ ] SELECT statements  
- [x] Administrative statements  
- [ ] Queries that use an index  
- [ ] Queries that use a join operation  

> **Explanation:** Administrative statements and queries not using indexes are not logged by default.

---

### 47. MULTIPLE CHOICE
**Which machine learning technique is NOT supported by HeatWave ML?**

- [ ] Anomaly Detection  
- [ ] Forecasting  
- [x] Clustering  
- [ ] Recommendation Systems  

> **Explanation:** HeatWave ML supports various ML techniques, but **not** Clustering.

---

### 48. MULTIPLE CHOICE
**From which cloud service can you use HeatWave?**

- [x] Amazon Web Services (AWS)  
- [ ] Google Cloud Platform (GCP)  
- [ ] Salesforce Cloud  
- [ ] IBM Cloud  

> **Explanation:** HeatWave can be used in Oracle Cloud, AWS, and Azure.

---

### 49. MULTIPLE CHOICE
**Which HeatWave feature allows you to query data from Object Storage?**

- [ ] High Availability  
- [ ] Read Replicas  
- [ ] Autopilot  
- [x] Lakehouse  

> **Explanation:** HeatWave Lakehouse supports querying data from Object Storage (Avro, CSV, JSON, Parquet).

---

### 50. MULTIPLE CHOICE
**Which action can you perform using the HeatWave service web-based console?**

- [ ] Write SQL code  
- [ ] Install MySQL Shell  
- [ ] Connect to MySQL Workbench  
- [x] Deploy your instances and manage their backups.  

> **Explanation:** HeatWave console lets you deploy instances, manage backups, and perform tasks without writing SQL.

---

### 51. MULTIPLE CHOICE
**Which database platform does HeatWave use to store OLTP data?**

- [ ] Oracle Database  
- [ ] Berkley DB  
- [x] MySQL  
- [ ] TimesTen In-Memory Database  

> **Explanation:** HeatWave uses **MySQL Enterprise Edition** to store OLTP data.
