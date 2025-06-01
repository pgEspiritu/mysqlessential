# 🔁 MySQL Replication Modes

## 1️⃣ Asynchronous Replication (Default Mode)

### 🔧 How It Works:
- The **source** commits a transaction and writes it to the **binary log**.
- The **replica’s I/O thread** reads the binary log via the **source's dump thread**.
- Events are stored in the **replica’s relay log**.
- The **replica’s SQL thread** applies changes to its own database.
- No **acknowledgment** is required from the replica.

### 🧩 Threads Involved:
- **Source:**
  - *Binary Log Dump Thread* – sends log events to replicas.
- **Replica:**
  - *I/O Thread* – fetches binary log events into relay log.
  - *SQL Thread* – reads relay log and applies transactions.

### ⚠️ Risk:
> If the source crashes **before** the replica receives the transaction, that transaction may be lost.

---

## 2️⃣ Semi-Synchronous Replication (Plugin-Based)

### 🔧 How It Works:
- Same initial process: source logs transaction and sends to replicas.
- **Before committing**, the source **waits for at least one replica** to acknowledge receipt of the transaction.
- Only **after acknowledgment** does the source commit and report success to the client.

### ✅ Key Benefit:
> Guarantees that **at least one replica** has the transaction if the source crashes immediately after commit.

### 💡 Additional Notes:
- Semi-synchronous replication is **not enabled by default**.
- Requires loading the plugin and enabling the appropriate configuration:

  ```ini
  [mysqld]
  rpl_semi_sync_master_enabled = 1
  rpl_semi_sync_slave_enabled = 1
  plugin_load_add = "semisync_master.so;semisync_slave.so"
  ```

---

## ⚖️ Comparison Summary

| Feature                     | Asynchronous                  | Semi-Synchronous                    |
|----------------------------|-------------------------------|-------------------------------------|
| Default Mode               | ✅ Yes                        | ❌ No (plugin required)             |
| Waits for Replica ACK      | ❌ No                         | ✅ Yes (at least one)               |
| Transaction Safety         | ⚠️ Potential data loss       | ✅ Improved safety                  |
| Performance                | ✅ Faster (no wait)           | 🔄 Slightly slower (waits briefly)  |
| Use Case                   | General replication           | High-availability setups            |
