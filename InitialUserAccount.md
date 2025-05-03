# 👤 MySQL Initial User Accounts & Configuration

Setting up MySQL user accounts and system-level users is a critical part of securing and configuring your MySQL installation. This guide covers account identifiers, installation behavior, and system user setup.

---

## 📛 MySQL Account Identifier

A MySQL user account is defined by **three elements**:

1. **Username** – Used by the client to log in.
2. **Hostname** – Specifies from where the user can log in.
3. **Password** – Required to authenticate access.

- The **hostname** can be:
  - A DNS name
  - An IP address
  - A **wildcard `%`** to allow access from any host
  - A partial IP using wildcards (e.g., `192.168.%`)

---

## 🛠️ System Accounts on Installation

Upon installation:

- MySQL creates **system-level accounts**.
- The main accessible account is usually the **`root`** administrative account 'root'@'localhost'.
- Depending on your installation method:
  - The **root password** is shown in the console or
  - Found in the **MySQL log file**

> 🔐 **Security Note**: You **must change** the root password before performing any operations.

---

## 🧑‍💻 MySQL Service User (System-Level)

The MySQL server process runs under a dedicated **system-level user**. Setup depends on the OS:

- **Windows Installer** and **Oracle Linux RPM** create this user automatically.
- With **generic binary distributions**, you must manually:
  - Create the system user (e.g., `mysql`)
  - Set up correct directory permissions

### Best Practices for MySQL System User

- Should **not** have admin or shell access
- Should **not** control network, mount drives, or manage system users
- **Requires**:
  - Read/write access to the **data directory**
  - Access to **log directories**
  - Access to **backup/scripts** directories (if used)

---

## 🗃️ Manual Setup Using Binary Archive

1. **Create OS User**  
   Example: `mysql`

2. **Create Directories**
   - MySQL binaries
   - Data directory

3. **Configure `my.cnf` File**
   - Define:
     - User
     - Data directory
     - Server settings

4. **Initialize MySQL**
   - Creates:
     - System databases
     - Server identity
     - Initial metadata

5. **Start the Server**
   - Use:
     - Binary executable
     - Startup scripts
     - Register as a system service

6. **Optional: Customize Startup**
   - Add command-line options
   - Modify service behavior
   - Extend configuration file as needed

> 🔗 Refer to [MySQL Installation Docs](https://dev.mysql.com/doc/) for detailed steps.

---

## 🔐 Security Tips

- Use a **dedicated system user** with:
  - No shell access
  - Minimal permissions
- Maintain **consistent file permissions**
  - Especially important when using tools like `sudo` for backup
