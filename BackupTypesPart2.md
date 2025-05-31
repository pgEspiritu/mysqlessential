# MySQL Enterprise Backup Overview

In this session, we'll go over how you can use **MySQL Enterprise Backup** for efficient and consistent backups.

---

## What is MySQL Enterprise Backup?

MySQL Enterprise Backup is a **physical backup** solution that offers:

- High performance for **large datasets**
- Faster than **logical backups** like `mysqldump`
- **Non-locking**: does not disrupt active systems during backup
- Supports **complete** and **partial backups** (specific databases)

---

## Backup Destinations and Features

### Supported Destinations

- **Local storage**
- **Cloud storage** (direct-to-cloud)
- **Tape** via **SBT** (System Backup to Tape)

### Key Features

- **Incremental backups** for faster processing
- **Point-in-time recovery** (PITR) – restore to a specific moment
- **Compression** – reduces storage requirements
- **Encryption** – ensures security and compliance
- **Optimistic backup** – handles busy tables separately for consistency and better performance

---

## Platform and Licensing

- Works on **all supported platforms**
- Requires a **MySQL Enterprise Edition license**
- Available as:
  - Part of MySQL Enterprise Edition
  - A **standalone package**

### How to Access

- Latest versions: [Oracle eDelivery](https://edelivery.oracle.com/)
- Previous releases: [My Oracle Support](https://support.oracle.com/)

---

## Version Compatibility

- **LTS Releases**:
  - Backup supports MySQL instances within the **same LTS release**
- **Innovation Releases**:
  - Supports the **previous LTS** and **subsequent innovation versions** within that family

---

## Monitoring with MySQL Enterprise Monitor

MySQL Enterprise Backup integrates with **MySQL Enterprise Monitor**, providing:

- A centralized **dashboard** for backup health and status
- Visibility into:
  - **Full backups**
  - **Partial backups**
  - **Incremental backups**
- Drill-down views into sub-operations of backup jobs
- **Alerts** for:
  - Backup **delays**
  - **Failures**
  - **Missed backups** based on your configured time intervals

---

✅ **Tip**: Use MySQL Enterprise Monitor for proactive tracking and operational confidence across your backup infrastructure.

