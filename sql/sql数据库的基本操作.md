# sql数据库的基本操作

tag: #sql/数据库

## create database

tag: #sql/更新/数据库/创建

The `CREATE DATABASE` statement is used to create a new SQL database.

```sql
CREATE DATABASE databasename;
```

## DROP DATABASE

tag: #sql/更新/数据库/删除

The `DROP DATABASE` statement is used to drop an existing SQL database.

```sql
DROP DATABASE databasename;
```

### TABLEG

#### create table

tag: #sql/更新/表/创建

The `CREATE TABLE` statement is used to create a new table in a database

```sql
CREATE TABLE table_name(
    colunm1 datatype,
    colunm2 datatype,
    ....
);
```

#### DROP TABLE

tag: #sql/更新/表/删除

The `DROP TABLE` statement is used to drop an existing table in a database.

```sql
DROP TABLE table_name;
```

#### ALTER TABLE

tag: #sql/更新/表/ALTER #sql/数据/修改/ALTER

- The `ALTER TABLE` statement is used to add, delete, or modify columns in an existing table.
- The `ALTER TABLE` statement is also used to add and drop various constraints on an existing table.

- ADD Column
	```sql
	ALTER TABLE table_name
	ADD colunm_name datatype;
	```
- DROP COLUMN
	```sql
	ALTER TABLE table_name
	DROP COLUMN colunm_name;
	```
- MODIFY COLUMN
	```sql
	ALTER TABLE table_name
	MODIFY COLUMN colunm_name datatype;
	```

