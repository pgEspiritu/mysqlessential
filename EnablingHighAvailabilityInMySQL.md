# High Availability with MySQL InnoDB Cluster

In this module, we will cover high availability configurations of MySQL servers using **InnoDB Cluster**.

By the end of this module, you'll understand:

- An overview of the InnoDB Cluster and how it enables high availability  
- The main components of an InnoDB Cluster  
- How the cluster handles failures, including a "split brain" scenario  
- How to monitor a highly available cluster  
- How InnoDB Cluster can be used in broader topologies alongside other replication configurations  

---

## 🔧 Introduction to InnoDB Cluster

**InnoDB Cluster** includes three major components that work together to provide high availability:

1. **Application Layer:** Clients connect to application servers, which typically include an API or web server.  
2. **MySQL Router:** Installed on application servers, it directs SQL queries to the correct MySQL instance based on cluster status.  
3. **MySQL Shell:** A versatile client used to manage and configure the cluster. It supports SQL, Python, and JavaScript.

Clustered server instances use **Group Replication** to share transactions virtually synchronously. The system manages conflict resolution, failure detection, and automatic recovery.

✅ InnoDB Cluster runs on any system that supports MySQL.

---

## 🏗️ Setting Up the Cluster

1. Use **MySQL Shell** to create a cluster and check its status.
2. Add at least **three MySQL instances** (on separate physical hosts).
3. Enable **Group Replication** for inter-server communication.
4. Configure **MySQL Router** on each application server using the `--bootstrap` option.

---

## 🔄 Automatic Failover with MySQL Router

In case of **primary server failure**:

- Applications are **not affected** since they connect via the **MySQL Router**, not directly to the server.
- **MySQL Router** detects the failure and automatically redirects traffic to a new primary server.
- **Failover** is handled entirely by the cluster.
- No need to reconfigure the application!

This seamless experience is a key benefit of using InnoDB Cluster for high availability.

---

## ⚙️ Hardware and Redundancy Considerations

- All nodes should have **similar hardware specs**.
- Prioritize **database performance** – avoid running other services on DB hosts.
- Always deploy **at least three nodes** (best in odd numbers like 3, 5, 7, or 9).
- Use **SSD storage** where possible.
- Avoid single points of failure:
  - Redundant **storage arrays**
  - Dual **power supplies**
  - Multiple **NICs and switches**

---

## 🌐 Cluster Topology Integration

InnoDB Cluster can be integrated into a broader MySQL environment using other replication topologies (e.g., asynchronous or semi-synchronous replication). This allows you to build flexible, globally distributed, and resilient architectures.

---

## 📌 Summary

- InnoDB Cluster provides built-in high availability for MySQL databases.
- MySQL Router ensures seamless application connectivity and automatic failover.
- Use MySQL Shell for cluster setup and management.
- Design your infrastructure for redundancy and performance.
