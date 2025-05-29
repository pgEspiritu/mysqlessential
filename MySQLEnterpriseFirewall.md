# 🔥 MySQL Enterprise Firewall

In this topic, we'll introduce **MySQL Enterprise Firewall**, a tool for **learning** and **protecting** the SQL statements that your server executes.

MySQL Enterprise Firewall can be enabled on **MySQL Enterprise Edition** via a plugin. It uses an **allow list** to set policies for acceptable queries. This allow list can be applied to either **specific accounts** or **groups**.

---

## 🚧 Real-Time Query Protection

- Every query executed on the server is verified in **real time**.
- The firewall checks that each query matches the structures defined in the allow list.
- **Only transactions matching well-formed, allowed queries are permitted.**
- **SQL injection attacks** and other unauthorized statements are automatically **blocked**.

If a query violates the policy:

- It is blocked immediately.
- A **real-time alert** is logged to the MySQL error log, offering visibility into possible security threats.

---

## 🧠 Learning Mode

MySQL Enterprise Firewall has a **Learning Mode**, which allows you to:

- Train the firewall by executing **known good queries** during development.
- Automatically populate the allow list based on this known workload.

This simplifies allow list creation before deploying your application to production.

---

## 🛡️ Transparent Operation

- Your application **does not require any changes** to work with the firewall.
- Queries are submitted as usual, and the firewall monitors them in the background.
- This adds a **transparent layer of protection** against SQL injection and unauthorized access.

The protection extends to:

- **Application SQL statements**
- Any **MySQL client** using the configured user

---

## 🔍 Example Use Case

Imagine you have an allow list policy that permits:

```sql
SELECT * FROM employee WHERE id = ?
```

If a user attempts:

```sql
SELECT * FROM employee WHERE id = 1 OR 1=1
```

This query will be blocked because it does not match the allowed structure.
Such an attempt might be made by a malicious user trying to bypass access controls.

---

## 🧪 Detect Bugs and Weaknesses

Sometimes, malformed or malicious queries are only possible due to **application bugs in data validation**. The MySQL Enterprise Firewall can help mitigate these issues by:

- **Detecting invalid or malicious queries**
- **Logging alerts in real time**
- **Helping you identify and fix bugs**, even if the attacks are already blocked

This results in:

- Improved **application resilience**
- Faster **incident response**

