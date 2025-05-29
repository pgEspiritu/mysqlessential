# MySQL Enterprise Security Products: Audit, Firewall, and Encryption

This module introduces key security-focused components in the **MySQL Enterprise Edition**. These tools help organizations comply with security regulations and protect sensitive data.

---

## 🔐 MySQL Enterprise Audit

### 📌 **Overview**
MySQL Enterprise Audit is an auditing extension that provides detailed visibility into:
- **Connections** and authentication events
- **Database operations** (e.g., queries, schema changes)
- **User activities** for compliance with regulations like **GDPR**, **NIS2**, **HIPAA**, and more.

It helps answer:
- **Who** did something?
- **What** did they do?
- **When** did they do it?
- **Where** did they connect from?

---

### ⚙️ **Key Features**

- **Real-Time Auditing:** No server restart required to enable, disable, or modify audit settings.
- **Flexible Output Formats:**  
  - `XML` or `JSON` format for easy integration with analysis tools.
- **Filtering Capabilities:**  
  - Customize what gets logged using filters for connections, queries, user actions, and schema changes.
  - Reduce noise and improve performance by excluding unimportant events.
- **Audit Log Protection:**  
  - Logs can be encrypted and compressed to protect identities and save space.
  - Access to audit logs is controlled to prevent tampering.
- **Rotating Logs:**  
  - Supports log rotation policies to prevent disk space exhaustion.
- **Deployment Options:**  
  - Available as a **component** or as a **legacy plugin**.

---

### 🔄 **Audit Workflow**

1. **Enable Plugin or Component:**

   ```sql
   INSTALL COMPONENT 'file://component_audit';
   ```

2. **Configure Filters:**

   Create rules to monitor:
  - Authentication attempts
  - SQL queries
  - Schema changes

3. **Audit in Action:**

  Logs are automatically created for each configured event.
  You can view them using:
  - MySQL Workbench
  - External XML/JSON parsers
  - SIEM or Audit Vault systems

# 🔥 MySQL Enterprise Firewall

The **MySQL Enterprise Firewall** is a security extension that helps **detect**, **block**, and **log** unauthorized or unexpected SQL statements. It’s particularly effective in defending against SQL injection attacks and enforcing policy-based query execution.

---

## 🧠 How It Works

The Firewall monitors SQL statements executed by users and learns their typical behavior. Based on this, it builds **whitelists of approved statements**.

Modes of operation:

| **Mode**         | **Purpose**                                                                 |
|------------------|------------------------------------------------------------------------------|
| **Learning Mode** | Observes SQL statements and builds a trusted ruleset.                       |
| **Protecting Mode** | Blocks statements not in the ruleset.                                      |
| **Recording Mode** | Continues normal operations while logging all SQL activity for analysis.   |
| **Disabled Mode**  | Turns off the firewall for specified users or globally.                    |

---

## 🛡️ Use Cases & Benefits

### ✅ **SQL Injection Protection**  
Block unauthorized SQL statements in real-time, reducing application-level vulnerabilities.

### ✅ **User Behavior Profiling**  
Track and enforce the expected SQL behavior for users or applications.

### ✅ **Compliance Enforcement**  
Prevent users from running queries outside their authorized patterns.

### ✅ **Low Overhead**  
Minimal impact on performance thanks to its efficient query pattern matching.

---

## ⚙️ Setup Overview

1. **Enable the Plugin:**

```sql
INSTALL PLUGIN mysql_firewall SONAME 'mysql_firewall.so';
```

2. **Set Learning Mode:**
```sql
CALL mysql.sp_set_firewall_mode('user@host', 'LEARNING');
```

3. **Run Typical Workload:**
Let the user/application run its normal queries.;

4. **Switch to Protecting Mode:**
```sql
CALL mysql.sp_set_firewall_mode('user@host', 'PROTECTING');
```

# 📝 What Gets Logged?

When in **Recording Mode** or **Protecting Mode**, firewall logs include:

- **User and host**
- **SQL statement attempted**
- **Date and time**
- **Whether it was blocked or allowed**

You can export these logs for further analysis or compliance audits.

---

## 💡 Example: Enable and Learn

```sql
CALL mysql.sp_set_firewall_mode('employee_user@localhost', 'LEARNING');
-- Run app normally
CALL mysql.sp_set_firewall_mode('employee_user@localhost', 'PROTECTING');
```
