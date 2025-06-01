# 🖥️ Multi-Server Topologies with MySQL InnoDB Cluster

This guide covers the configuration of multi-server topologies in MySQL InnoDB Cluster and related technologies, including single-primary and multi-primary modes, ReplicaSets, InnoDB ClusterSet, read replicas, and Kubernetes deployments.

---

## ⚙️ Single-Primary Mode

- All **write operations** go to the single-primary server (e.g., Server S1).
- **Reads** can be load-balanced across other servers.
- If the primary fails:
  - Write operations pause until automatic failover occurs.
  - Cluster selects a new primary (e.g., Server S2).
  - Routers reconfigure and clients connect to the new primary.

[Learn more about failover process](#)

---

## 🔄 Multi-Primary Mode

- Any server can act as primary, distributing both reads and writes.
- Failure of a server does **not** block clients connected to others.
- Routers update topology automatically; clients reconnect as needed.
- **Conflict handling:**
  - Conflicting transactions on the same row: only one is applied.
  - Table locks are **not** shared across members, which can cause conflicts.
  - Avoid simultaneous schema changes on multiple members.
  - Avoid cascading foreign key constraints (e.g., `ON DELETE CASCADE`), which may cause conflicts.

---

## 🔗 MySQL ReplicaSet

- Uses **MySQL replication** instead of group replication.
- Single-primary server with MySQL Router for query routing.
- Provides read scaling and load balancing benefits.
- Configure using **MySQL Shell Admin API**:
  - Add, configure, and remove members.
  - Supports automatic member provisioning.
- **No automatic failover:** manual switchover required on failure.

[More about ReplicaSets](#)

---

## 🌐 InnoDB ClusterSet (Multi-Site Clusters)

- Connects multiple InnoDB Clusters, typically across sites.
- Each cluster has its own high availability and automatic failover.
- Recovery Point Objective (RPO) = 0 for intra-site failures (no data loss).
- Recovery Time Objective (RTO) usually seconds (failover reconfiguration time).
- Cross-site replication is **asynchronous**, so RPO > 0 (some data loss possible).
- Failover across sites is manual or external-automated.
- Manage cluster topology online with Admin API — no app code changes required.

---

## 📈 Read Replicas

- Add scalability and disaster recovery to any topology.
- Serve **read-only** queries; no commit delays or conflicts.
- Populated **asynchronously** from source servers.
- Can promote replicas to cluster members if needed.
- Configurable via MySQL Shell and usable by MySQL Router for read traffic.

---

## ☸️ Hosting MySQL on Kubernetes

- Lightweight alternative to full virtualization.
- MySQL servers and routers run in **pods** on worker nodes.
- Kubernetes provides portability, extensibility, and automation.
- Use manifests for easy, version-controlled configuration.
- Rolling upgrades and cluster scaling can be managed smoothly.

---

## 🛠️ MySQL Operator for Kubernetes

- Fully featured management tool for InnoDB Clusters on Kubernetes.
- Supports:
  - Automatic deployment of servers and routers.
  - Self-healing and backup/restore.
  - Sequenced operations and rolling upgrades with minimal downtime.
  - Scaling cluster members with configurable consistency.
- Installable via **Helm** package manager.

---

## 📚 Summary

- InnoDB Clusters provide **high availability** with group replication, routing, and monitoring.
- Failover mechanisms prevent split-brain scenarios.
- Multiple topology configurations address diverse deployment needs.
- Kubernetes and Operator tools streamline management at scale.
