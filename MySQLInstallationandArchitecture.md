# MySQL Installation and Architecture

This module covers the steps and concepts necessary for preparing, installing, and maintaining MySQL across various environments and platforms.

---

## 📌 Module Overview

By the end of this module, you will be able to:

- Prepare your environment for MySQL installation.
- Choose the appropriate software edition.
- Install MySQL on Linux or Windows.
- Create initial user accounts.
- Understand and configure MySQL settings.
- Upgrade MySQL between versions or editions.

---

## 🖥️ Preparing the Environment

- **Supported OS**: Linux, Windows, macOS.
- **Deployment Options**:
  - Physical servers
  - Virtual Machines (VMs)
  - Containers (Docker, Kubernetes)
  - MySQL HeatWave on various clouds
- **Performance Features**:
  - Multithreading support
  - Non-Uniform Memory Access (NUMA)
  - InnoDB storage engine uses a buffer pool for faster data access.
  - SSD and solid-state storage are fully utilized.

---

## 🛡️ Redundancy and Reliability

- Redundant hardware is critical:
  - Power supplies
  - Network connections
  - Storage media
- Prevents single points of failure and maximizes uptime.

---

## 📦 MySQL Editions

### Community Edition
- Free and open-source
- Most popular for web applications
- Available at: [https://www.mysql.com](https://www.mysql.com)

### Enterprise Edition
- Commercial version with Oracle support
- Includes enterprise-only features
- Available via:
  - [Oracle Support](https://support.oracle.com)
  - [Oracle eDelivery](https://edelivery.oracle.com) (for trial)

### Source Code
- Available on:
  - [MySQL.com](https://dev.mysql.com)
  - [GitHub](https://github.com/mysql)

---

## 🔁 Release Model

### Long-Term Support (LTS)
- Example: MySQL 8.4
- New LTS every 2 years
- Supported for up to 8 years
- Feature-stable and backward compatible

### Innovation Releases
- Released quarterly
- Contains new cutting-edge features
- Must upgrade more frequently
- Fully production-ready

---

## 🧰 MySQL Tools and Connectors

- Language-specific **connectors** connect your apps to MySQL.
- Always use the **latest version** for best compatibility.
- Work with all supported MySQL versions.

---

## ☁️ Containers and Virtualization

- Supports:
  - Docker
  - Virtual Machines
- Image sources:
  - **Community**: [Docker Hub](https://hub.docker.com/_/mysql)
  - **Enterprise**: Docker Store, Oracle Container Registry

---

## 📚 Documentation and Resources

- **Reference Manuals**: [dev.mysql.com](https://dev.mysql.com)
- **Oracle Knowledge Base**: [support.oracle.com](https://support.oracle.com)
- **Blogs**:
  - Community updates by [lefred](https://lefred.be/)
  - Performance insights by [Dimitri Kravchuk](https://dimitrik.free.fr/blog/)

---

## ✅ Summary

This module equips you with essential knowledge to:
- Choose the right MySQL edition.
- Prepare and optimize your installation.
- Use the correct tools and stay updated.
- Understand release strategies for long-term and rapid innovation use cases.

---
