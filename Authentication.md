# MySQL User Authentication  

MySQL authenticates users by storing account details in a system database. User accounts are identified using three elements:

- **Username**  
- **Hostname** (often separated by an `@` sign)  
- **Password**  

---

## 🛠️ **Account Identifier**  

- The account identifier is structured as `username@host`.  
- The **host identifier** specifies where the user can connect from:  
  - A DNS hostname (e.g., `localhost`, `mydomain.com`).  
  - An IP address (e.g., `192.168.1.10`).  
  - Wildcards (`%`) can be used to allow connections from multiple hosts.  

**Examples:**  
- `test@localhost` — User `test` can only connect from localhost.  
- `admin@%` — User `admin` can connect from any host.  
- `user@192.168.%` — User `user` can connect from any IP in the `192.168.x.x` range.  

---

## ✅ **Creating a User**  

To create a new user, use the `CREATE USER` statement.  
Example:  

```sql
CREATE USER 'test'@'%' IDENTIFIED BY 'password123';
```

- test can connect from any host (`%`).
- The `IDENTIFIED` BY clause sets the user's password.

---

## 🔐 Password Storage and Encryption
MySQL does not store plain text passwords.
- It uses a secure, one-way encryption algorithm.
- The default algorithm is `caching_sha2_password`.

---

## 📦 Changing Authentication Algorithm
- You can use a different authentication algorithm by setting the `default_authentication_plugin` variable in the `my.cnf` or `my.ini` file:
Example to set the authentication plugin to MySQL native password:

```ini
[mysqld]
default_authentication_plugin = mysql_native_password
```

---

## 📝 Examples of User Management
1. Create a user that can only log in from localhost:
   
```sql
CREATE USER 'local_user'@'localhost' IDENTIFIED BY 'securePass!';
```

2. Change the password for an existing user:

```sql
ALTER USER 'test'@'%' IDENTIFIED BY 'newPassword456';
```

3. Change your own password (current session user):

```sql
SET PASSWORD = 'myNewSecurePassword!';
```

4. Create a user with a specific authentication plugin:

```sql
CREATE USER 'legacy_user'@'%' IDENTIFIED WITH mysql_native_password BY 'legacyPass123';
```

---

## 🔗 Additional Resources:
- [MySQL User Security](https://dev.mysql.com/doc/refman/8.0/en/security.html)
- [MySQL Authentication Plugins](https://dev.mysql.com/doc/refman/8.0/en/authentication-plugins.html)
- [MySQL Password Security](https://dev.mysql.com/doc/refman/8.0/en/password-security.html)

