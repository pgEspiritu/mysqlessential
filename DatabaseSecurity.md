# Database Security in MySQL  

In this module, we'll introduce one of the most important topics in **database security**. By the end of this module, you should be able to:  
- Understand how **MySQL enables compliance** with various regulatory frameworks.  
- Identify and mitigate some of the more common **security risks**.  
- **Authenticate to the database** by configuring users and setting passwords.  
- Learn how MySQL Enterprise Edition enables integration with **external authentication mechanisms and roles**.  
- **Authorize accounts** to perform various tasks with data and database administration.  

---

## 🔒 Regulatory Compliance in MySQL  

MySQL provides features that help organizations comply with key international regulations. Some well-known regulations include:  
- **GDPR** (General Data Protection Regulation)  
- **HIPAA** (Health Insurance Portability and Accountability Act)  
- **Sarbanes-Oxley Act** (SOX)  
- **UK Data Protection Act**  
- **NIS2** (Network and Information Systems Directive 2)  

---

### ✅ Key Requirements for Compliance  

Although each regulatory framework has specific requirements, they generally include the following:  

- **Monitoring User Activity:**  
  - Track user creation, schema changes, and backup activities.  

- **Data Protection:**  
  - Ensure databases are encrypted at **REST**.  
  - Restrict access to authorized users only.  

- **Retention Policies:**  
  - Define policies for secure backup storage and controlled data use.  

- **Audit Access:**  
  - Maintain logs of data access and modifications to track who accessed or modified records.  

---

### 📦 MySQL Features for Compliance  

MySQL offers compliance features through:  
- Core **Community Edition** features.  
- Additional **Enterprise Edition** features, including advanced authentication, audit logging, and encryption options.  
