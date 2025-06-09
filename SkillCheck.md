# MySQL Quiz

---

### 1. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which statement is true about the data directory?**

- [ ] It is configured automatically when you install MySQL from binary archive.  
- [ ] It is a mandatory setting in the my.cnf file.  
- [ ] It is empty until you create a user database.  
- [x] It contains the my.cf and temporary files.  

> **Explanation**:  
The data directory setting `datadir` specifies the default location of system and user databases, and is one of the settings for file locations. Other settings include locations for temporary files and configuration files.

---

### 2. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which installation method requires that you manually configure the service user?**

- [ ] MySQL Installer  
- [x] binary archive  
- [ ] RPM packages  
- [ ] yum packages  

> **Explanation**:  
The `yum` and `RPM` package installers install and configure MySQL on Linux. The MySQL Installer installs and configures MySQL on Windows. The binary archive only contains the necessary files but does not perform any configuration.

---

### 3. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which statement is true about upgrades?**

- [ ] You can upgrade MySQL while the server is running.  
- [x] You can upgrade MySQL while the server is offline by replacing the binaries with new versions.  
- [ ] You must reinstall MySQL completely and restore from backup when upgrading from Community Edition to Enterprise Edition.  
- [ ] The Upgrade Checker utility is only available in Enterprise Edition.  

> **Explanation**:  
Upgrading is an offline operation, performed in-place by replacing existing binaries. This also works when upgrading to Enterprise Edition. The Upgrade Checker utility is available in MySQL Shell for all editions.

---

### 4. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**How often are MySQL Innovation versions released?**

- [ ] Every month  
- [x] Every quarter  
- [ ] Every year  
- [ ] Every two years  

> **Explanation**:  
MySQL long-term support versions are released every two years. Innovation versions are released quarterly.

---

### 5. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which permissions are required for the MySQL service user?**

- [ ] Root privileges  
- [ ] System privileges  
- [ ] Shell privileges  
- [x] Data directory privileges  

> **Explanation**:  
The MySQL service user needs only privileges to run the process and access the necessary directories and network. No extra permissions should be granted.

---

### 6. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**For which language does MySQL Shell offer support?**

- [ ] PHP  
- [ ] GO  
- [ ] JAVA  
- [x] Python  

> **Explanation**:  
MySQL Shell supports JavaScript, Python, and SQL for scripting and automation.

---

### 7. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which statement is true about MySQL Workbench Enterprise?**

- [ ] It installs MySQL server.  
- [ ] It adds security features to the MySQL system.  
- [ ] It backs up MySQL instances.  
- [x] It simplifies MySQL database migrations.  

> **Explanation**:  
Workbench Enterprise helps simplify migrations with integrated tools.

---

### 8. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which service does MySQL HeatWave offer?**

- [ ] Automatic replication to the Oracle Database  
- [ ] Backup to GitHub  
- [ ] Migration to AWS Aurora  
- [x] Fully managed MySQL service  

> **Explanation**:  
MySQL HeatWave provides a fully managed MySQL cloud service with key database management features.

---

### 9. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**When is MySQL Enterprise Support available?**

- [ ] 8 hours a day, 5 days a week  
- [ ] 8 hours a day, 7 days a week  
- [ ] 24 hours a day, 5 days a week  
- [x] 24 hours a day, 7 days a week  

> **Explanation**:  
Support is available 24/7 to ensure timely help.

---

### 10. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**How many major editions does MySQL offer?**

- [ ] 5  
- [ ] 1  
- [x] 2  
- [ ] 3  

> **Explanation**:  
MySQL offers Community Edition (free) and Commercial Edition (paid).

---

### 11. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**What does the Oracle commercial licensing option allow businesses to do?**

- [ ] Use MySQL Enterprise Edition for free  
- [x] Use MySQL in their products with other third-party commercial products  
- [ ] Pay a reduced price for MySQL Community Edition  
- [ ] Use MySQL code in their products and keep their code private  

> **Explanation**:  
Oracle’s commercial license allows closed-source use of MySQL in commercial products.

---

### 12. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**What is performed by the JOIN clause in SQL?**

- [ ] Concatenates two or more column values  
- [x] Connects rows from two or more tables on some condition  
- [ ] Jumps to the next row if a value is null  
- [ ] Generates a Venn diagram  

> **Explanation**:  
JOIN connects rows from multiple tables using conditions.

---

### 13. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which data type stores string values?**

- [ ] DOUBLE  
- [ ] BIT  
- [x] ENUM  
- [ ] DECIMAL  

> **Explanation**:  
ENUM stores predefined string values.

---

### 14. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which statement is true about PRIMARY indexes?**

- [ ] They speed up insert operations.  
- [ ] You can have multiple PRIMARY indexes on a table.  
- [x] PRIMARY index values are replicated to every secondary index.  
- [ ] You can have multiple rows with the same value in the PRIMARY index.  

> **Explanation**:  
Primary index values are unique and used by secondary indexes for lookups.

---

### 15. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which is the default MySQL storage engine?**

- [x] InnoDB  
- [ ] MyISAM  
- [ ] NDB Cluster  
- [ ] Memory  

> **Explanation**:  
InnoDB is the default and supports transactions and foreign keys.

---

### 16. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**What can you accomplish using MySQL Partitioning?**

- [ ] Specify how big each table can be  
- [ ] Specify how big each column can be  
- [x] Specify a physical file for each row based on a rule  
- [ ] Specify the storage engine per database  

> **Explanation**:  
Partitioning allows distributing rows across physical storage based on rules.

---

### 17. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**What is the default MySQL authentication plugin used to encrypt passwords?**

- [ ] caching_sha256_password  
- [ ] mysql_native_password  
- [x] caching_sha2_password  
- [ ] plaintext  

> **Explanation**:  
`caching_sha2_password` is secure and used by default.

---

### 18. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which type of compliance do GDPR, HIPAA, FERPA, and GLBA impose that MySQL can implement?**

- [ ] Administrative  
- [x] Regulatory  
- [ ] Performance  
- [ ] Financial  

> **Explanation**:  
These laws define regulatory compliance that MySQL can help achieve.

---

### 19. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which statement about dynamic privileges is true?**

- [ ] Assigned in mysqld-auto.cf  
- [x] Assigned by server/plugin/component at load  
- [ ] Assigned implicitly by transaction needs  
- [ ] Assigned in my.cnf  

> **Explanation**:  
Dynamic privileges are granted by the server, plugins, or components at runtime.

---

### 20. MULTIPLE CHOICE  
⏱ 45 sec • 🏅 1 pt  

**Which MySQL Enterprise feature supports Kerberos, PAM, and FIDO?**

- [ ] Auditing  
- [ ] Firewall  
- [ ] Manager  
- [x] Authentication  

> **Explanation**:  
MySQL Enterprise Authentication supports external methods like LDAP, PAM, Kerberos, and FIDO.

---

# MySQL Enterprise Multiple Choice Answers

---

### 21. Which product can mitigate the risk of SQL Injection attacks?
- [x] MySQL Enterprise Firewall  
- [ ] MySQL Enterprise Audit  
- [ ] Oracle Enterprise Manager  
- [ ] MySQL Shell  

---

### 22. In which two ways can you install the MySQL Enterprise Masking and De-Identification feature?
- [x] Plugin  
- [x] Component  
- [ ] Stored Procedure  
- [ ] Configuration File  
- [ ] Tablespace  

---

### 23. Against what does MySQL Enterprise Firewall provide real-time protection?
- [ ] Virus  
- [ ] Denial of Service (DoS) Attack  
- [x] SQL Injection  
- [ ] Brute Force Attack  

---

### 24. When using MySQL Enterprise Transparent Data Encryption (TDE), which key must be stored outside the database?
- [x] Master  
- [ ] Private  
- [ ] Public  
- [ ] Tablespace  
- [ ] Primary  

---

### 25. Which two formatting options are supported by MySQL Enterprise Audit?
- [ ] Text  
- [x] JSON  
- [x] XML  
- [ ] YAML  
- [ ] SQL  

---

### 26. What file can you encrypt using MySQL Enterprise Transparent Data Encryption (TDE)?
- [ ] Configuration File (my.cnf or my.ini)  
- [ ] SSL Key File  
- [ ] General Query, Slow Query, and Error Log File  
- [x] Tablespace File  

---

### 27. What makes a database backup effective?
- [ ] Scheduling the backup  
- [ ] Monitoring the backup for consistency  
- [ ] Not exceeding limitations for the backup resources  
- [x] Being able to restore the backup data  

---

### 28. What must you do to restore from a backup using MySQL Enterprise Backup?
- [ ] Review the SQL script generated to make sure it is valid.  
- [ ] Unzip the MySQL Enterprise Backup file.  
- [ ] Shut down the MySQL database system.  
- [x] Remove any previous files from the MySQL data directory.  

---

### 29. What is the MySQL Enterprise Backup utility designed for?
- [ ] Create a snapshot of the MySQL storage medium  
- [ ] Perform upgrades of MySQL systems  
- [ ] Create Logical backup of MySQL systems  
- [x] Create Physical backup of MySQL systems  

---

### 30. Which statement is true about the mysqldump utility?
- [ ] mysqldump is a standard way to create physical backups.  
- [ ] mysqldump is excellent for backing up large databases.  
- [ ] mysqldump is fast and does not require locking tables.  
- [x] The mysqldump output is a human-readable text file with SQL statements.  

---

### 31. How does MySQL Enterprise Backup support optimistic backup?
- [ ] It locks up tables during the backup process.  
- [ ] It ignores data from busy tables.  
- [ ] It puts the database server in read-only mode.  
- [x] It records all data including data from busy tables.  

---

### 32. What is one requirement on the source to enable source-replica replication?
- [x] Source must have binary logging enabled.  
- [ ] Source must have the sql_require_primary_key variable set to on.  
- [ ] Source must have all tables use InnoDB storage engine only.  
- [ ] Source must have its binary log format set to statement based.  

---

### 33. Which thread is responsible for taking a copy of the binary log events from the source and writing those to a relay log?
- [x] I/O thread  
- [ ] I/O binlog dump thread  
- [ ] SQL thread  
- [ ] Connection thread  

---

### 34. What uses the Relay Log?
- [ ] Source  
- [x] Replica  
- [ ] Both Source and Replica  
- [ ] Neither  

---

### 35. Which thread maintains an open connection to the source when the replica connects and is used to send the binary log contents from the source to a replica?
- [ ] I/O thread  
- [ ] Connection thread  
- [ ] SQL thread  
- [x] I/O binlog dump thread  

---
