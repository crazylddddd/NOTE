# SELECT 的执行过程

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [SELECT 的执行过程](#select-的执行过程)
  - [查询的结构](#查询的结构)
  - [SELECT 的执行顺序](#select-的执行顺序)
  - [SQL 的执行原理](#sql-的执行原理)

<!-- /code_chunk_output -->

## 查询的结构

```mermaid
flowchart TD
    subgraph one
    a[select....] ---> b["from(从哪些表中选择)....."]
    b ---> c["where(多表的连接条件)"...]
    c ---> d["and(不包含组函数的过滤条件)"...]
    d ---> e["group by(分组的依据)"]
    e ---> f["having(包含组函数的过滤条件)"]
    f ---> g["order by(排序)" ... asc/desc]
    g ---> h["limit(分页)"]
    end
    subgraph two
    a2[select....] ---> b2["from(从哪些表中选择)....JOIN..."]
    b2 ---> b3["ON(多表的连接条件/去除笛卡尔积)"]
    b3 ---> c2["where(不包含组函数的过滤条件)"...]
    c2 ---> d2["and/or(不包含组函数的过滤条件)"...]
    d2 ---> e2["group by(分组的依据)"]
    e2 ---> f2["having(包含组函数的过滤条件)"...]
    f2 ---> g2["order by(排序)" ... asc/desc]
    g2 ---> h2["limit(分页)"]
    end
```

## SELECT 的执行顺序

```mermaid
flowchart LR
    FROM ---> WHERE
    WHERE ---> GB[GROUP BY]
    GB ---> HAVING
    HAVING ---> field[SELECT的字段]
    field ---> DISTINCT
    DISTINCT ---> OB[ORDER BY]
    OB ---> LIMIT
```

- 在执行步骤的时候，每个步骤都会产生一个**虚表(vt)**,作为下一个步骤的输入(且用户不可见)

## SQL 的执行原理

```mermaid
flowchart TD
    table["t1(table1)"] --> t1
    subgraph FROM[FROM阶段]
    t1 ---> step(通过CROSS JOIN求笛卡尔积)
    step ---> vt1-1
    vt1-1 -->|通过ON筛选| vt1-2
    vt1-2 -->|外连接添加外部行| vt1
    vt1 -->|如果有多张表重复此阶段| step
    end
    vt1 -->|WHERE阶段筛选| vt2
    vt2 -->|GROUP和HAVING阶段,分组和分组过滤| vt3,vt4
    vt3,vt4 -->|SELECT和DISTINCT阶段,提取字段和过滤重复行| vt5-1,vt5-2
    vt5-1,vt5-2 -->|ORDER BY阶段,排序| vt6
    vt6 -->|LIMIT阶段| vt7
```
$$f(x)=\int_0^xxd(x)$$