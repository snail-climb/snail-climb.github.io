# MySQL基础语法

## 1. SQL语法分类

- DDL（Data Definition Language）：数据定义语言
- DML（Data Manipulation Language）：数据操纵语言
- DQL（Data Query Language）：数据查询语言
- DCL（Data Control Language）：数据控制语言

## 2. DDL

### 2.1 DDL操作数据库

> DDL操作数据库主要进行增删查操作

#### 2.1.1 创建数据库

- 创建数据库

```mysql
CREATE DATABASE 数据库名称;

CREATE DATABASE IF NOT EXISTS 数据库名称;
```

#### 2.1.2 删除数据库

- 删除数据库

```mysql
DROP DATABASE 数据库名称;

DROP DATABASE IF EXISTS 数据库名称;
```

#### 2.1.3 查询数据库

- 查询所有数据库

```mysql
SHOW DATABASES;
```

#### 2.1.4 使用数据库

- 使用数据库

```mysql
USE 数据库名称;
```

- 查看当前使用的数据库

```mysql
SELECT DATABASE();
```

### 2.2 DDL操作数据表

> DDL操作数据表主要进行增删改查操作

#### 2.2.1 创建表

- 创建表

```mysql
CREATE TABLE 表名 (
	字段名1 数据类型1,
	字段名2 数据类型2,
    ...
	字段名n 数据类型n
);
```

#### 2.2.2 删除表

- 删除表

```mysql
DROP TABLE 表名;

DROP TABLE IF EXISTS 表名;
```

#### 2.2.3 修改表

- 添加列

```mysql
ALTER TABLE 表名 ADD 列名 数据类型;
```

- 删除列

```mysql
ALTER TABLE 表名 DROP 列名;
```

- 修改表名

```mysql
ALTER TABLE 表名 RENAME TO 新表名;
```

- 修改数据类型

```mysql
ALTER TABLE 表名 MODIFY 列名 新数据类型;
```

- 修改列名和数据类型

```mysql
ALTER TABLE 表名 CHANGE 列名 新列名 新数据类型;
```

#### 2.2.4 查询表

- 查询当前数据库下所有表

```mysql
SHOW TABLES;
```

- 查询表结构

```mysql
DESC 表名称;
```

## 3. DML

> DML主要是对数据进行增删改操作

### 3.1 新增数据

- 对指定列新增数据

```mysql
INSERT INTO 表名(列名1,列名2,...,列名n)
VALUES(值1,值2,...,值n);
```

- 对全部列新增数据

```mysql
INSERT INTO 表名
VALUES(值1,值2,...,值n);
```

- 批量新增数据

```mysql
INSERT INTO 表名(列名1,列名2,...,列名n)
VALUES(值1,值2,...,值n),
VALUES(值1,值2,...,值n),
...
VALUES(值1,值2,...,值n);



INSERT INTO 表名
VALUES(值1,值2,...,值n),
VALUES(值1,值2,...,值n),
...
VALUES(值1,值2,...,值n);
```

### 3.2 删除数据

- 删除数据

```mysql
DELETE FROM 表名
[WHERE 条件];
```

### 3.3 修改数据

- 修改数据

```mysql
UPDATE 表名
SET 列名1 = 值1, 列名2 = 值2, ..., 列名n = 值n
[WHERE 条件];
```

## 4. DQL

> DQL主要是对数据进行查询操作

### 4.1 完整语法

```mysql
SELECT
	字段列表
FROM
	表名列表
WHERE
	条件列表（分组前条件）
GROUP BY
	分组字段
HAVING
	分组后条件
ORDER BY
	排序字段（默认：ASC，即升序）
LIMIT
	分页设置
```

### 4.2 基础查询

- 查询多个字段

```mysql
SELECT 字段1, 字段2, ..., 字段n FROM 表名;
```

- 查询所有字段

```mysql
SELECT * FROM 表名;
```

- 别名

```mysql
SELECT 字段1 AS 别名1, 字段2 AS 别名2, ..., 字段n AS 别名n FROM 表名; -- AS也可省略
```

- 去重

```mysql
SELECT DISTINCT 字段列表 FROM 表名;
```

### 4.3 条件符号

| 符号                | 描述                                                   |
| ------------------- | ------------------------------------------------------ |
| >                   | 大于                                                   |
| <                   | 小于                                                   |
| =                   | 等于                                                   |
| >=                  | 大于或等于                                             |
| <=                  | 小于或等于                                             |
| != 或 <>            | 不等于                                                 |
| BETWEEN ... AND ... | 在某个范围内（闭区间）                                 |
| IN()                | 多选一                                                 |
| LIKE                | 模糊查询（`_`:代表单个任意字符，`%`:代表任意个数字符） |
| IS NULL             | 是NULL                                                 |
| IS NOT NULL         | 非NULL                                                 |
| AND 或 &&           | 与                                                     |
| OR 或 \|\|          | 或                                                     |
| NOT 或 !            | 非                                                     |

### 4.4 聚合函数

| 聚合函数 | 描述     |
| -------- | -------- |
| count()  | 统计数量 |
| max()    | 最大值   |
| min()    | 最小值   |
| sum()    | 求和     |
| avg()    | 平均值   |

### 4.5 分页查询

- 语法

```mysql
SELECT 字段列表 FROM 表名 LIMIT 起始索引, 每页查询条数;
```

> 起始索引计算公式：
>
> **起始索引 = (当前页码 - 1) * 每页查询条数**

