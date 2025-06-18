# ⚙️ Installing MySQL on Your Operating System

MySQL supports multiple platforms. You can install it on:

- Various **Linux** or **Unix** distributions  
- **Windows**  
- **macOS**  
- **Oracle Linux (UEK)**  
- **Solaris**  
- **FreeBSD**

📝 **Complete installation and configuration instructions are available at:**  
[https://dev.mysql.com/doc/refman/en/installing.html](https://dev.mysql.com/doc/refman/en/installing.html)

---

## 🪟 Installing MySQL on Windows

### 🔧 Option 1: MySQL Installer (Recommended)
- Wizard-based interface
- Installs:
  - MySQL Server
  - MySQL Workbench
  - MySQL Shell
  - Sample databases
  - Documentation and admin tools
- Lets you select:
  - Installation location
  - Components
  - Initial configuration

### 🧱 Option 2: Binary ZIP Archive
- Includes only MySQL binaries
- Requires manual configuration:
  - Windows service setup
  - MySQL configuration file (`my.ini`)

---

## 🐧 Installing MySQL on Linux

### 🧩 Options Vary by Distribution

- Use **native package managers**:
  - `yum` / `dnf` on Oracle Linux, CentOS, RHEL
  - `apt` on Debian-based distros (e.g., Ubuntu)
- Or install from **binary archives** for full control

---

### 🧪 Choosing the Right Method

| Factor | Use Package Manager | Use Binary Archive |
|--------|---------------------|--------------------|
| Simplicity | ✅ Yes | ❌ No |
| Customization | ⚠️ Limited | ✅ High |
| Recommended for Beginners | ✅ Yes | ❌ No |

Some distributions use **MySQL forks** by default. Ensure you're using the **official MySQL repository** if you want Oracle's version.

---

### 🔗 Common Dependencies on Linux

Installed automatically via package manager:

- `libaio` – async I/O operations
- `libtinfo` – console text output handling

---

## 🗂️ Linux Installation Paths (Oracle Linux RPM Example)

| Path | Description |
|------|-------------|
| `/var/lib/mysql` | Data directory (InnoDB logs, databases) |
| `/usr/bin` | MySQL client, admin tools |
| `/etc/my.cnf` | Main server-wide config |
| `/etc/init.d/mysql` | Init script (SysVinit systems) |
| `systemd` configs | Used in modern distros for service management |
| `/var/log/mysqld.log` | Error log (human-readable) |

---

## 🔌 MySQL Enterprise Edition on Linux

- Must be downloaded **manually** (no public repo)
- Oracle customers can create internal repo using a **dedicated installer package**

---

## 🔧 Extending MySQL Functionality

### 🧱 Plugins
- Tight integration with MySQL server APIs
- Add:
  - Global/system variables
  - Server functions

### 🧩 Components
- Service-based architecture
- Modular, loosely coupled from core server

### 🧮 Additional Extensibility Options

- Stored Procedures
- Triggers
- User-defined Functions (UDFs)

---

## ✅ Summary

- Choose installer method based on your OS and level of control needed
- Use package managers when possible for simplicity and automated dependency handling
- Use binary archives when you require complete installation flexibility
- Always validate you're installing **official MySQL** and not a fork, unless explicitly intended
- Extend MySQL using built-in features or by loading plugins/components

---

📘 **Next Steps**: Configure users, services, and system integration.
