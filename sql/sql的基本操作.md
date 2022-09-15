# mysql的基本操作

---

## 查询

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

## 使用WHERE

- WHERE 用来过滤数据
- 可以跟**AND**,**OR**,**NOT**操作符组合

```sql
SELECT column1,column2..
FROM table_name
WHERE condition;
```

> Note: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!

---

## 通过ORDER BY排序

- 可以通过使用ORDER BY + 关键字排序

```sql
SELECT column1,column2...
FROM table_name
ORDER BY column1,column2..... ASC|DESC;
```

---

## 插入数据

-使用INSERT INTO语法插入数据

```sql
INSERT INTO table_name(column1,column2....)
VALUES (valuse1,valuse2,...);
```

---

## 更新数据

- 使用UPDATE语法更新数据

```sql
UPDATE table_name
SET column1 = valuse1 column2 = valuse2.....
WHERE condition;
```

---

## 删除数据

- 使用DELETE语法删除数据

```sql
DELETE FROM table_name WHERE condition;
```

---

## 限制返回数

- 使用LIMIT语法来限制返回数

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```

---

## 使用LIKE

- The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.
- There are two wildcards often used in conjunction with the LIKE operator:
  - The percent sign (%) represents zero, one, or multiple characters
  - The underscore sign (_) represents one, single character

```sql
SELECT column1,column2...
FROM table_name
WHERE condition LIKE pattern;
```