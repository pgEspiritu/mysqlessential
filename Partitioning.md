## Table Partitioning

We'll finish this module with a short look at **partitioning**. Table partitioning is enabled by using a plugin. When you partition a table, you divide its content according to certain rules. You might store portions of the table based on the range of values in a column. For example, storing all sales for 2024 in a single partition.

### Types of Partitioning

- **Range Partitioning**: A partition based on a range allows you to store portions of the table based on a range of values. For instance, sales data from different years might be stored in different partitions.

- **List Partitioning**: A partition based on a list enables you to store rows with specific values in the partition column. For example, you can store data for specific regions or departments in different partitions.

- **Hash/Key Partitioning**: When you partition by hash or key, you distribute rows somewhat evenly between partitions. This means that you can distribute a large table across multiple disks, or you can place more frequently accessed data on faster storage.

### EXPLAIN with Partitioning

The `EXPLAIN` command works with partitioning. Simply prefix any query that uses partitioned data with `EXPLAIN`, and the output will show information about how the optimizer will use the partition. 

### Note
Partitioning is one of the features that is only fully supported in **Enterprise Edition**.

## Conclusion

This concludes this module on **data design**. In this module, you learned about:
- **Data storage**,
- **Databases (schemas)** and **tables** with their data types,
- **Indexes** for improving performance,
- **Queries that join multiple tables**, and
- A quick look at **table partitioning**, allowing you to distribute data in a single table across multiple partitions.
