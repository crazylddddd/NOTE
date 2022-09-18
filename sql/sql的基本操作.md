# mysql 的基本操作

---

## 查询

#sql/查询/数据/SELECT

### 查询所有数据

```sql
SELECT * FROM table_name;
```

### 查询部分数据

```sql
SELECT column1,column2....
FROM table_name;
```

---

## 使用 WHERE

#sql/查询/数据/过滤/WHERE

- WHERE 用来过滤/数据g数据
- 可以跟**AND**,**OR**,**NOT**操作符组合

```sql
SELECT column1,column2..
FROM table_name
WHERE condition;
```

> Note: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!

---

## 通过 ORDER BY 排序

#sql/查询/数据/排序/ORDER_BY

- 可以通过使用 ORDER BY + 关键字排序

```sql
SELECT column1,column2...
FROM table_name
ORDER BY column1,column2..... ASC|DESC;
```

---

## 插入数据

#sql/更新/数据/插入/INSERT_INTO

-使用 INSERT INTO 语法插入数据

```sql
INSERT INTO table_name(column1,column2....)
VALUES (value1,value2,...);
```

---

## 更新数据

#sql/更新/数据/UPDATE 

- 使用 UPDATE 语法更新数据

```sql
UPDATE table_name
SET column1 = value1 column2 = value2.....
WHERE condition;
```

---

## 删除数据

#sql/更新/数据/删除/DELETE

- 使用 DELETE 语法删除数据

```sql
DELETE FROM table_name WHERE condition;
```

---

## 限制返回数

#sql/查询/数据/显示/LIMIT

- 使用 LIMIT 语法来限制返回数

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```

---

## 使用 LIKE

#sql/查询/数据/过滤/LIKE

- The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.
- There are two wildcards often used in conjunction with the LIKE operator:
  - The percent sign (%) represents zero, one, or multiple characters
  - The underscore sign (\_) represents one, single character

```sql
SELECT column1,column2...
FROM table_name
WHERE condition LIKE pattern;
```

### 通配符

| symbol | description                        |
| ------ | ---------------------------------- |
| **%**  | represents zero or more characters |
| **-**  | represents a single character      |

## 使用 IN

#sql/查询/数据/过滤/IN

- The IN operator allows you to specify multiple values in a WHERE clause.
- The IN operator is a shorthand for multiple OR conditions.

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1,value2.....);
```

## 使用 BETWEEN

#sql/查询/数据/过滤/BETWEEN

- The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.
- The BETWEEN operator is inclusive: begin and end values are included.

```sql
SELECT column_name(s)
FROM table_name
where column_name between value1 AND value2
```

## 使用 Aliases

#sql/别名/AS

- Aliases are used to give a table, or a column in a table, a **temporary** name.
- Aliases are often used to make column names more **readable**.
- An alias only exists for the **duration** of that query.
- An alias is created with the **AS** keyword.

```sql
SELECT column_name AS alias_name
FROM table_name;
```

## 使用JOINS

#sql/查询/数据/过滤/JOIN

- A `JOIN` clause is used to **combine rows** from two or more tables, **based on a related column** between them


-    `INNER JOIN`: Returns records that have matching values in both tables
-   `LEFT JOIN`: Returns all records from the left table, and the matched records from the right table
-   `RIGHT JOIN`: Returns all records from the right table, and the matched records from the left table
-   `CROSS JOIN`: Returns all records from both tables

![[joins.png]]

### INNER JOIN

#sql/查询/数据/过滤/INNER_JION

- The `INNER JOIN` keyword selects records that have matching values in both tables.

![[INNER_JOIN.png]]

```sql
SELECT column_name(s)  
FROM table1  
INNER JOIN table2  
ON table1.column_name = table2.column_name;
```

### LEFT JOIN

#sql/查询/数据/过滤/LEFT_JOIN

- The `LEFT JOIN` keyword returns all records from the left table (table1), and the matching records (if any) from the right table (table2).

![[LEFT_JOIN.png]

```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name=table2.column_name;
```

### RIGHT JOIN

#sql/查询/数据/过滤/RIGHT_JOIN

- The `RIGHT JOIN` keyword returns all records from the right table (table2), and the matching records：(if any) from the left table (table1).

![[RIGHT_JOIN.png]]

```sql
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name=table2.column_name;
```

### CROSS JOIN

#sql/查询/数据/过滤/CROSS_JOIN

- The `CROSS JOIN` keyword returns all records from both tables (table1 and table2).

![[CROSS_JOIN.png]]

```sql
SELECT column_name(s)
FROM table1
CROSS JOIN table2
```

**Note:** `CROSS JOIN` can potentially return very large result-sets!

### SELF JOIN

#sql/查询/数据/过滤/SELF_JOIN

- A self join is a regular join, but the table is joined with itself.

```sql
SELECT _column_name(s)_  
FROM _table1 T1, table1 T2_  
WHERE _condition_;
```

**_T1_ and _T2_ are different table aliases for the same table.**

## 使用UNION

#sql/查询/数据/过滤/UNION

The `UNION` operator is used to combine the result-set of two or more `SELECT` statements.

-   Every `SELECT` statement within `UNION` must have the same number of columns
-   The columns must also have similar data types
-   The columns in every `SELECT` statement must also be in the same order
- The `UNION` operator selects only distinct values by default. To allow duplicate values, use `UNION ALL`:

**Note:** The column names in the result-set are usually equal to the column names in the first `SELECT` statement.

```sql
SELECT column_name FROM table1
UNION
SELECT column_name FROM table2


SELECT column_name FROM table1
UNION ALL
SELECT column_name FROM table2
```

## GROUP BY

#sql/查询/数据/分类/GROUP_BY

The `GROUP BY` statement groups rows that have the same values into summary rows, like "find the number of customers in each country".

The `GROUP BY` statement is often used with aggregate functions (`COUNT()`, `MAX()`, `MIN()`, `SUM()`, `AVG()`) to group the result-set by one or more columns.

```sql
SELECT column_name 
FROM table_name 
WHERE condition 
GROUP BY column_name
ORDER BY column_name;
```

## HAVING

#sql/查询/数据/过滤/HAVING

The `HAVING` clause was added to SQL because the `WHERE` keyword cannot be used with aggregate functions.

```sql
SELECT column_name 
FROM table_name 
WHERE Condition 
GROUP BY col
HAVING Condition 
ORDER BY column_name 
```

