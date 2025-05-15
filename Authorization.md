# MySQL User Authorization and Privileges  

In this section, we'll explore how to authorize users to perform specific tasks in MySQL using the `GRANT` statement, manage privileges at different levels, and handle potential access issues.  

---

## ✅ **Granting Privileges to Users**  

The `GRANT` statement is used to assign specific privileges to users. The syntax is:  

```sql
GRANT privilege_type ON object_type TO user [WITH GRANT OPTION];
```

- `privilege_type`: The type of operation (e.g., `SELECT`, `INSERT`, `UPDATE`).
- `object_type`: The level of access (e.g., database, table, column).
- `user`: The user to whom the privilege is granted.
- `WITH GRANT OPTION`: Allows the user to pass on the granted privileges to other users.

---

## 🔵 Global Privileges:
Granting privileges at the server level:

```sql
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;
```

- This grants full access to all databases and tables for the user `admin`.

## 🟢 Database-Level Privileges:
Granting privileges for a specific database:

```sql
GRANT CREATE, ALTER, DROP ON `sales_db`.* TO 'sales_admin'@'localhost';
```

- This grants `CREATE`, `ALTER`, and `DROP` privileges only on the sales_db database.

## 🟡 Table-Level Privileges:
Granting privileges for a specific table:

```sql
GRANT SELECT, INSERT ON `sales_db`.`orders` TO 'sales_clerk'@'%';
```

- This grants `SELECT` and `INSERT` privileges for the `orders` table to the `sales_clerk` user.

## 🟠 Column-Level Privileges:
Granting privileges for specific columns:

```sql
GRANT SELECT (`customer_name`, `order_total`) ON `sales_db`.`orders` TO 'sales_clerk'@'%';
```

- This allows the `sales_clerk` user to `SELECT` only the `customer_name` and `order_total` columns.

## 🟣 Stored Procedure Privileges:
Granting execution privileges for a stored procedure:

```sql
GRANT EXECUTE ON PROCEDURE `sales_db`.`calculate_discount` TO 'sales_clerk'@'%';
```

- This allows the `sales_clerk` user to run the `calculate_discount` procedure.

---

## 🚨 Handling Locked Accounts and Forgotten Passwords
If the root account password is forgotten, the server can be started with the --skip-grant-tables option to reset it:

1. Stop the MySQL Server:
```bash
sudo systemctl stop mysqld
```

2. Start MySQL with Skip Grant Tables:

```bash
mysqld_safe --skip-grant-tables &
```

3. Connect to MySQL as Root:

```bash
mysql -u root
```

4. Reset the Root Password:

```sql
FLUSH PRIVILEGES;
ALTER USER 'root'@'localhost' IDENTIFIED BY 'NewSecurePassword';
```

5. Restart the MySQL Server:
   
```bash
sudo systemctl restart mysqld
```

---

## 🛠️ Dynamic Privileges
MySQL includes several dynamic privileges that can be enabled or disabled at runtime.

Example of Dynamic Privileges:
- `REPLICATION SLAVE`: Allows replication from a master server.
- `FIREWALL ADMIN`: Administer the MySQL Enterprise Firewall.

**Granting a Dynamic Privilege:**
```sql
GRANT REPLICATION SLAVE ON *.* TO 'repl_user'@'192.168.1.100';
```

---

## 🛡️ Plugin-Specific Privileges
Plugins and components can define additional privileges.
- Example:
    - `FIREWALL ADMIN`: Defined by the MySQL Enterprise Firewall plugin.
    - `AUDIT ADMIN`: Defined by the MySQL Enterprise Audit plugin.

**Granting Plugin-Specific Privileges:**
```sql
GRANT FIREWALL ADMIN ON *.* TO 'firewall_admin'@'localhost';
```

---

## 🧩 Revoking Privileges
To remove privileges from a user, use the REVOKE statement:

```sql
REVOKE SELECT ON `sales_db`.`orders` FROM 'sales_clerk'@'%';
```

---

## 🔄 Flushing Privileges
If you make changes to the privilege system outside of the GRANT or REVOKE statements, run:

```sql
FLUSH PRIVILEGES;
```

---

## 🔗 Additional Resources:

- [MySQL Dynamic Privileges](https://dev.mysql.com/doc/refman/8.0/en/grant.html#grant-dynamic-privileges)



