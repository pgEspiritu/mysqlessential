# 🛠️ Tools for Monitoring MySQL

In this section, we'll look at **built-in tools and features** you can use to monitor MySQL efficiently. These tools help identify slow queries, analyze performance bottlenecks, and ensure overall database health.

---

## 🐢 Slow Query Log

The **Slow Query Log** records queries that take a long time to execute. It’s one of the simplest and most useful tools to detect performance issues.

### 🔧 Key Variables

- `long_query_time`  
  Queries that take longer (in seconds) than this value are logged.

- `min_examined_row_limit`  
  Queries that examine more than this many rows are logged.

### 📌 Optional Logging

- `log_slow_admin_statements`  
  Logs administrative statements (e.g., `ANALYZE`, `OPTIMIZE`) that are slow.

- `log_queries_not_using_indexes`  
  Logs queries that don’t use any indexes.

> 🔎 **Tip:** Use this log to spot inefficient queries and then **optimize or rewrite** them.

---

## 📝 Summarizing Slow Queries

Use the following utility to analyze your slow query log:

```bash
mysqldumpslow [options] /path/to/slow_query.log
```

## 📈 Performance Schema

The **Performance Schema** is a powerful internal system database designed to provide **low-level execution statistics**.

### ⚙️ Key Features

- Does **not store data on disk** — data is in memory and reset on restart  
- Uses its own fast **in-memory storage engine**  
- Not replicated to other systems  
- Uses **fixed-size ring buffers** (when full, it overwrites old data)  

### 📌 Tracks

- Query execution  
- Wait events (e.g., I/O, locks)  
- Threads and memory usage  
- Stored procedure activity  

---

## 📊 SYS Schema

The **SYS Schema** complements the Performance Schema by providing **simplified, human-readable views and procedures**.

### 🔍 What SYS Schema Offers

- Prebuilt **views for I/O hotspots**  
- Insight into **blocking/locking issues**  
- Reports on **heavy queries and high-load tables**  
- Diagnoses **index usage inefficiencies**  
- Helps with **server health monitoring**  

> 💡 **Note:** The SYS schema depends on the **Performance Schema** being enabled.

---

## ✅ Summary

| Tool               | Purpose                          | Notes                            |
|--------------------|----------------------------------|----------------------------------|
| **Slow Query Log** | Identify slow queries            | Adjustable logging thresholds    |
| **mysqldumpslow**  | Summarize slow query log         | Helps prioritize optimizations   |
| **Performance Schema** | Fine-grained performance insights | In-memory, not persistent     |
| **SYS Schema**     | Simplified monitoring            | Friendly views & procedures      |

---

By using these tools, you can monitor query performance, detect slowdowns, and proactively optimize your MySQL environment.
