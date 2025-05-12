## Table Joins

Next, we'll have a brief look at queries that join tables together. You can run a query that looks at multiple tables based on some condition. The most common type of table join is an **inner join**. 

### Inner Join
If you have two tables, A and B, an **inner join** shows only those rows in table A that meet some condition in table B, and vice versa. 

The graphic represents this as a Venn diagram, where only the intersection of the two tables is highlighted. 

#### Example:
The query examines two tables, `Employees` and `Orders`. It shows the employee's last name and how many orders they've taken. Notably, it does not show any employees who have not yet taken orders, nor any orders without a registered employee because it is an inner join.

```sql
SELECT e.last_name, COUNT(o.order_id) 
FROM Employees e
INNER JOIN Orders o ON e.employee_id = o.employee_id
GROUP BY e.last_name;
```
---

### Left Outer Join
A left outer join shows the same rows from the inner join, as well as many rows from the left table that are not already in that list. The left table is a table whose name comes before or to the left of the `JOIN` keyword. In the example syntax, the left table is `Employees`.

This query shows the last name of each employee and the number of orders they have taken. It differs from the first query in that we also see employees who have not yet taken an order.

```sql
SELECT e.last_name, COUNT(o.order_id) 
FROM Employees e
LEFT OUTER JOIN Orders o ON e.employee_id = o.employee_id
GROUP BY e.last_name;
```
---

### Right Outer Join
A right outer join shows the same rows from the inner join and adds any rows from the right table that are not already in that list. In the example syntax, the right table is `Orders`.

This query shows the employee last name and the order ID for every order. If the order does not yet have a registered employee, the employee last name will be `NULL`.

```sql
SELECT e.last_name, o.order_id 
FROM Employees e
RIGHT OUTER JOIN Orders o ON e.employee_id = o.employee_id;
```
---

## Additional Join Types
### Left Join Example
This first example is a left join, showing all columns from the join set of `emp LEFT JOIN orders`. That is, it shows all employees and the orders they have taken, including employees who have not yet taken an order.

```sql
SELECT * 
FROM Employees e
LEFT JOIN Orders o ON e.employee_id = o.employee_id;
```

### Semijoin Example
The second example only shows those employees who have not yet taken an order. It does not include any of the rows that would be included in an inner join. This is sometimes called a semijoin.

```sql
SELECT * 
FROM Employees e
LEFT JOIN Orders o ON e.employee_id = o.employee_id
WHERE o.order_id IS NULL;
```

### Right Join Example
We can do the same on the right too. The third example is a right join, again showing all employees and the orders they have taken, plus any orders that do not yet have a registered employee.

```sql
SELECT * 
FROM Employees e
RIGHT JOIN Orders o ON e.employee_id = o.employee_id;
```

### Right Semijoin Example
The right semijoin shows only those orders that do not yet have a registered employee, again leaving out the rows that would be included in an inner join.

```sql
SELECT * 
FROM Orders o
LEFT JOIN Employees e ON e.employee_id = o.employee_id
WHERE e.employee_id IS NULL;
```

## EXPLAIN Command
The `EXPLAIN` command is useful to examine queries and how MySQL will process them. It shows which tables must be examined to answer the query. This is usually every join table. For each table examined, it shows which indexes are suitable for fulfilling the request.

It works with any DML statement, not just `SELECT`.

Example:
In the example, you see a `SELECT` statement that we have already seen. The only difference is that the `EXPLAIN` keyword has been prefixed. The output shows that MySQL will read through all the rows of the `emp` table. For each row, it will use the foreign key index to quickly find matching rows in the `Orders` table.

```sql
EXPLAIN 
SELECT e.last_name, COUNT(o.order_id) 
FROM Employees e
INNER JOIN Orders o ON e.employee_id = o.employee_id
GROUP BY e.last_name;
```

