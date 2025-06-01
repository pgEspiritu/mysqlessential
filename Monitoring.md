# 🚦 InnoDB Cluster Monitoring and Management

This document outlines how to monitor and manage MySQL InnoDB Clusters, focusing on cluster status, replication internals, and cluster-wide configuration using MySQL Shell.

---

## 🔍 Monitoring Cluster Status with Performance Schema

MySQL's **Performance Schema** provides detailed insights at both:

- 🧑‍🤝‍🧑 **Member level**
- 📋 **Transaction level**

This information is **shared across the cluster**, so you can query any member to get a full view of cluster health.

### 📊 Key Performance Schema Tables

- **`replication_group_members`**  
  Displays the status of each server in the cluster:

  | State         | Description                                                                                  |
  |---------------|----------------------------------------------------------------------------------------------|
  | ✅ `ONLINE`    | Server is synchronized and fully operational                                                |
  | 🔄 `RECOVERING`| Server is connected but not yet synchronized; cannot serve data                             |
  | ⚪ `OFFLINE`   | Server is connected but not part of the group                                               |
  | ❌ `ERROR`     | Server has issues preventing normal operations (e.g., missing transactions)                 |
  | 🚫 `UNREACHABLE`| Server cannot be contacted by the group                                                    |

- 🔗 **Connection and Applier Status Tables**  
  Provide detailed info about replication I/O and transaction execution per server.

---

## 🔄 Group Replication Communication Channels

Group Replication uses two separate channels:

1. 🛠️ **`group_replication_applier`**  
   Applies transactions originating from the group.

2. 🔧 **`group_replication_recovery`**  
   Handles topology changes and distributed recovery when nodes join or rejoin the group.

---

## ⚙️ Cluster Configuration Management

The cluster configuration metadata is stored in the `mysql_innodb_cluster_metadata` database, which is **replicated across all members** to ensure consistency.

### 👥 Cluster User Accounts

- The cluster automatically configures identical user accounts on every member for internal communication:
  - 🔐 **Cluster Administrator Account**
  - 🔑 **Router Administrator Account**

- All accounts have:
  - The same name
  - Identical permissions
  - The same password

- To reset all recovery account passwords cluster-wide, use MySQL Shell:

  ```js
  .resetRecoveryAccountsPassword()
  ```
# 🐚 Managing the Cluster with MySQL Shell

MySQL Shell enables cluster-wide operations without the need to log into individual servers.

## 💻 Useful MySQL Shell Functions

| Function                | Purpose                                                     |
|-------------------------|-------------------------------------------------------------|
| ⚙️ `configureInstance()`   | Sets cluster properties and configures admin/router accounts on a member |
| 🔧 `setupRouterAccount()`  | Configures router accounts on cluster members               |
| 👤 `setupAdminAccount()`   | Adds admin accounts if members are already configured       |

---

## 📋 Summary

| Topic                    | Details                                                      |
|--------------------------|--------------------------------------------------------------|
| 📊 Performance Schema      | Provides cluster-wide status on members and transactions     |
| 🔄 Group Replication Channels | `applier` for transactions, `recovery` for topology sync     |
| 💾 Cluster Metadata        | Stored and replicated in `mysql_innodb_cluster_metadata`      |
| 👥 User Accounts           | Uniform admin/router accounts on all members for communication |
| 🐚 MySQL Shell Management  | Centralized cluster configuration and user account management |

---

## 📚 Additional Resources

- [MySQL InnoDB Cluster Documentation](https://dev.mysql.com/doc/refman/en/mysql-innodb-cluster.html)  
- [MySQL Shell Admin API](https://dev.mysql.com/doc/mysql-shell/8.0/en/mysql-shell-admin-api.html)  
- [Performance Schema Tables](https://dev.mysql.com/doc/refman/8.0/en/performance-schema-tables.html)  
