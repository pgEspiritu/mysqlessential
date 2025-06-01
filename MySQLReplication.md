# 🌀 MySQL Replication Overview

## 🎯 Module Goals
By the end of this module, you will:
- Understand key MySQL replication concepts
- Explain the difference between **asynchronous** and **semi-synchronous** replication
- Identify how to set up different **replication topologies** to meet business needs

---

## 🔑 Key Concepts

### 🖥️ Roles
- **Source (formerly Master):** Receives writes from the application
- **Replica (formerly Slave):** Reads from the source; used for reads, backups, analytics, etc.

### 🔁 Replication Types
- **Asynchronous Replication**
  - Source does **not wait** for replicas before committing
  - Replication occurs **after** the transaction commits

- **Semi-Synchronous Replication**
  - Source waits for **at least one** replica to **acknowledge** receipt of the transaction
  - Improves consistency at the cost of latency

---

## 🧱 Topologies

- **Single Source → Multiple Replicas**
- **Multi-Source → Single Replica**
- **Ring or Chain Replication**
- **Hierarchical Tree Structure**

📌 *Adding replicas does **not** require source reconfiguration.*

---

## 💼 Use Cases for Replication

- **Load Balancing:** Distribute read operations across replicas
- **Scaling Out:** Add more replicas for read performance
- **Disaster Recovery:** Keep a hot standby server ready
- **High Availability:** Reconfigure apps to use replicas during failover
- **Analytics Offloading:** Run heavy queries on replicas
- **Distributed Business Units:** Share central data (e.g., products) while maintaining local data (e.g., inventory)

---

## ⚙️ Replication Setup (Quick Steps)

### ✅ On the **Source**:
1. **Create a replication user**:
   ```sql
   CREATE USER 'repl'@'%' IDENTIFIED BY 'password';
   GRANT REPLICATION SLAVE ON *.* TO 'repl'@'%';
    ```
2. **Enable Binary Logging & GTIDs (optional but recommended)**:
   - Ensure **log_bin** and **gtid_mode=ON** are enabled in **my.cnf**

3. Check log status:
   ```sql
    SHOW BINARY LOG STATUS;
    ```

---

## 📥 On the Replica:
1. **Set source info using**:
   ```sql
    CHANGE REPLICATION SOURCE TO
    SOURCE_HOST = 'source_host',
    SOURCE_USER = 'repl',
    SOURCE_PASSWORD = 'password',
    SOURCE_LOG_FILE = 'mysql-bin.000001',
    SOURCE_LOG_POS =  154;
    ```

2. **Start replication**:
   ```sql
    START REPLICA;
    ```
   
3. **Monitor replication**:
    ```sql
    SHOW REPLICA STATUS\G
    ```

## 🧠 Summary
- MySQL replication supports asynchronous and semi-synchronous modes.
- You can build flexible topologies for performance, availability, or scalability.
- Use cases include:
  - Load balancing
  - Failover
  - Analytics
  - Geographically distributed systems
- Setting up replication involves creating users, enabling logs, and configuring replicas.
