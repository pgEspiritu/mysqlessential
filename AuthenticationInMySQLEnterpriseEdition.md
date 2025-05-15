# MySQL Enterprise Authentication and Roles  

In this lesson, we'll explore how MySQL Enterprise Edition can integrate with external authentication systems and manage user roles.  

---

## 🔐 **Authentication Plugins in MySQL Enterprise Edition**  

MySQL Enterprise Edition supports several authentication mechanisms for centralized account management and authentication based on group membership and roles. These include:  

1. **LDAP (Lightweight Directory Access Protocol):**  
   - Enables connection to centralized LDAP services.  
   - Supports direct authentication with LDAP or through SASL (Simple Authentication and Security Layer).  

2. **PAM (Pluggable Authentication Module):**  
   - Standard authentication framework in Linux/Unix.  
   - Allows authentication via LDAP, Kerberos, and other methods.  
   - Supports proxy user configuration, enabling indirect login through a PAM service.  

3. **Windows Authentication:**  
   - Uses Active Directory for authentication.  
   - Maps Windows user accounts to MySQL users.  

4. **FIDO Authentication:**  
   - Passwordless authentication using biometric or hardware security tokens.  

---

## 🌐 **LDAP Authentication**  

LDAP authentication enables centralized user management through LDAP servers.  

**Example:**  
- Joe logs into the application using LDAP credentials.  
- Application sends credentials to MySQL.  
- MySQL binds to the LDAP server using native LDAP plugin and verifies Joe’s identity.  

**Command Example:**  
```sql
CREATE USER 'joe'@'%' IDENTIFIED WITH 'auth_ldap_simple' AS 'joe_ldap';
```

---

## 🛠️ PAM Authentication
PAM allows flexible authentication using Linux/Unix authentication modules.

Example Process:
- Joe logs in using a PAM service named mysql.
- MySQL forwards credentials to the configured PAM service.
- PAM service verifies the credentials using LDAP, Kerberos, or other methods.

**Command Example:**
```sql
CREATE USER 'joe'@'localhost' IDENTIFIED WITH 'auth_pam' AS 'mysql';
```

---

## 🖥️ Windows Authentication
Windows authentication leverages Active Directory to authenticate users.

Example Process:
- Joe logs into Windows using domain credentials.
- Application passes security context to MySQL.
- MySQL verifies the context with the domain controller and maps the Windows user to the MySQL user.

**Command Example:**
```sql
CREATE USER 'win_joe'@'%' IDENTIFIED WITH 'auth_windows';
```

---

## 📦 Roles in MySQL
Roles are collections of privileges that can be assigned to multiple users or other roles.

**Creating Roles:**
```sql
CREATE ROLE 'admin_db1', 'app_updater', 'r1';
```

**Assigning Roles to Users:**
```sql
CREATE USER 'app_middleware_db1'@'localhost';
GRANT 'admin_db1', 'app_updater' TO 'app_middleware_db1'@'localhost';
```

**Assigning the `WITH ADMIN OPTION:`**
- Allows the user to manage the role's membership.
```sql
GRANT 'r1' TO 'app_middleware_db1'@'localhost' WITH ADMIN OPTION;
```

**Assigning Roles to Other Roles:**
```sql
GRANT 'admin_db2t1' TO 'admin_db1';
```

---

## Viewing Role Hierarchies:
- MySQL allows exporting role relationships as a graph for better visualization.

**Example Command:**
```sql
SHOW GRANTS FOR 'app_middleware_db1'@'localhost';
```

---

## Managing Multiple Entities:
- Multiple roles or users can be added in a single command.
```sql
GRANT 'admin_db1', 'app_updater' TO 'user1'@'localhost';
```

---

## Revoking Roles:
- Revoke specific roles from users:
```sql
REVOKE 'app_updater' FROM 'app_middleware_db1'@'localhost';
```

---

🔗 Additional Resources:

- [MySQL Authentication Plugins](https://dev.mysql.com/doc/refman/8.0/en/authentication-plugins.html)
- [MySQL Role-Based Access Control](https://dev.mysql.com/doc/refman/8.0/en/roles.html)
- [MySQL PAM Pluggable Authentication](https://dev.mysql.com/doc/refman/8.4/en/pam-pluggable-authentication.html)

