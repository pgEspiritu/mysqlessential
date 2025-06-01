# MySQL Replication Topologies

## Common Configurations

### 1. Source-to-Source Replication
- Two servers replicate both to and from each other.
- Suitable when different applications (e.g., customer-facing store and warehouse management) need access to the same data.
- Risk: concurrent writes to same rows can cause data inconsistency.
- Mitigation: use mutually exclusive identifiers (e.g., auto-increment even IDs on one server, odd on the other).

### 2. Chain Topology
- A hierarchy of replication, where data flows from one server to the next.
- Useful when upstream servers (e.g., warehouse) serve data to downstream servers (e.g., customer-facing store).
- Final servers (e.g., analytics or BI) receive all combined data.

### 3. Ring Topology
- Each server is both a source and a replica of another.
- An extended version of source-to-source replication.
- Risk of corruption exists due to potential concurrent writes.
- Can be used for high availability with semi-synchronous replication.

### 4. Multi-Source Replication
- A single replica replicates from multiple sources using multiple channels.
- Each source has its own channel, copying a binary log to the replica.
- Ideal for consolidating distributed data (e.g., game servers sending data to a central analytics server).
- Requires conflict resolution strategies (e.g., de-conflicting unique IDs).

## Dynamic Replication Controls
- You can dynamically add or modify replication filters per channel.
- You can change the source of a replication channel at runtime.

## Summary
- MySQL replication allows for flexible deployment topologies.
- Modes: Asynchronous (default) and Semi-Synchronous (plugin-based).
- Topologies support use cases like:
  - Load balancing
  - Disaster recovery and failover
  - Analytics and reporting
  - Geographical data aggregation
