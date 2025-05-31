# MySQL Backup Strategies

In this module, we will discuss backing up your MySQL instances. By the end of this module, you will be able to:

- Distinguish between the different types of backups available.
- Understand the advantages and disadvantages of each backup type.
- Understand the benefits of the **MySQL Enterprise Backup** utility available with **MySQL Enterprise Edition**.

---

## Why Do We Back Up?

The whole point of a database is to store and retrieve your business data—your intellectual property.

Backing up your data enables:

- **Disaster recovery** after catastrophic events
- **Error recovery**, reverting to a previous known-good state
- **System migration**
- **Replication** for load balancing or parallel systems
- **Data archiving**
- **Historical reporting**
- **Test environments** for development

---

## Backup Planning Considerations

Designing a reliable backup strategy requires careful planning:

- **Resource Management**: Backups require memory, disk I/O, and CPU. These add load to your system.
- **Downtime Avoidance**: Schedule backups during off-peak hours.
- **Storage**: Consider whether to use network or local storage.
- **Monitoring**: Ensure backups succeed via logging, alerts, and consistency checks.
- **Restoration Testing**: A backup is only useful if you can restore from it.
- **Compliance**: Align backups with data retention policies and regulatory requirements.

> Every backup is a snapshot of your data at a specific moment and is subject to the same data policies.

---

## Logical Backup

A **logical backup** creates a script of SQL statements that recreate the structure and data of the database. 

### Characteristics:

- Must be **created and restored on a running server**
- Slower than physical backups
- Easier to move across systems

### Tools:

- `mysqldump` – creates SQL statements
- `MySQL Shell` – exports data in formats like CSV or JSON

---

## Physical Backup

A **physical backup** is a copy of the actual data files used by the server.

### Considerations:

- Copying files while the server is active can lead to **inconsistent state**
- Inconsistent backups may trigger **crash recovery**
- Requires stable file state for consistency

### Tools:

- **MySQL Enterprise Backup** – ensures consistency during live backups
- **File System Copy or Snapshot** – requires server shutdown or crash recovery

---

## Additional Backup Techniques

- **Binary Logs** – allow **point-in-time recovery**
- **Replication** – replica acts as a backup; can be paused to freeze state
- **Replication Lag** – maintains a time-delayed replica
- **Transportable Tablespaces** – copy specific tables or table sets to another server

---

## Backup Types

### Full Backup

- Complete copy of the database at a given time
- **Slow** to back up and restore
- Required as the base for incremental or differential backups

### Incremental Backup

- Contains only changes **since the last backup**
- Requires full backup + all intermediate incremental backups to restore
- Efficient storage, but **slower to restore**

### Differential Backup

- Contains all changes **since the last full backup**
- Larger over time but **faster to restore**
- Only the last full backup and the latest differential backup are required

---

## Summary

Choosing the right combination of logical, physical, incremental, and differential backups can help you build a robust, efficient, and compliant MySQL backup strategy tailored to your needs.
