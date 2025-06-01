# Split-Brain and Network Partitioning in InnoDB Cluster

## Understanding Split-Brain

A **split-brain** occurs when the network splits the cluster into multiple partitions that cannot communicate with each other. This is **not** a host failure but a network failure scenario.

### Normal Operation (No Partition)
- Assume a cluster of **5 nodes** (always an odd number).
- Transactions arrive at the **primary node**.
- When a transaction commits, it is replicated **to all nodes**.
- Each node maintains an up-to-date copy of the data.
- Every transaction from any client applies on the primary and replicates successfully to all other nodes.

---

## What Happens During a Network Partition?

- The cluster splits into partitions — typically a **larger partition** and a **smaller partition** (due to odd number of nodes).
- Without any protection:
  - Transactions on the primary are only replicated to nodes within the same partition.
  - Clients connected to other partitions might apply transactions on **different primaries**.
- This leads to **split-brain**: two independent clusters with **diverging data**, making the database unreliable.

---

## How Group Replication Prevents Split-Brain

Group Replication includes built-in protection against split-brain:

- Nodes detect when other nodes are **unreachable**.
- The partition **without the majority** of nodes goes **offline**.
- The **majority partition**:
  - Continues running.
  - Selects a new primary if needed.
- Routers connected to the majority partition automatically redirect traffic to this partition.

**In simple terms:**  
> The cluster only functions if a **majority** of nodes stay connected. If the majority is lost, that partition shuts down.

---

## Example: Network Partition with 9 Nodes

- A majority means at least **5 out of 9** nodes.
- If network splits into:
  - Partition A: 5 nodes → continues operating.
  - Partition B: 4 nodes → shuts down.
- Neither partition can communicate with the other.

---

## Other Scenarios

- If a single server fails/disconnects in a 9-node cluster:
  - The cluster becomes an 8-node cluster.
  - Majority is still 5.
  - The cluster automatically reconfigures routers accordingly.
  - It can tolerate up to 3 more failures before losing majority.

---

## Cluster Size and Fault Tolerance

| Group Size | Minimum Members | Maximum Members | Failures Tolerated for HA |
|------------|-----------------|-----------------|---------------------------|
| Smallest   | 3               | 3               | 1                         |
| Typical    | 3, 5, 7, or 9   | 9               | Depends on majority count  |

- The **minimum number of members** in a group is **3**.
- You can configure clusters with 3, 5, 7, or 9 nodes initially.
- If a single node fails, the cluster may temporarily have an even number of members until recovery.

---

## Summary

| Concept           | Description                                                 |
|-------------------|-------------------------------------------------------------|
| **Split-brain**   | Network partition causes multiple primaries and inconsistent data. |
| **Group Replication** | Protects by allowing only the majority partition to operate.     |
| **Majority Rule** | Cluster runs only if majority of nodes are connected.       |
| **Fault Tolerance**| Depends on the number of nodes; larger clusters tolerate more failures. |

---

*High availability depends on maintaining a majority of healthy, connected nodes in the cluster.*

