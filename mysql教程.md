# MySQL 教程

MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

- 1.数据以表格的形式出现
- 2.每行为各种记录名称
- 3.每列为记录名称所对应的数据域
- 4.许多的行和列组成一张表单
- 5.若干的表单组成database

- **主键**：主键是唯一的。一个数据表中只能包含一个主键。你可以使用主键来查询数据。
- **外键：**外键用于关联两个表。

# MySQL 安装

- **MySQL** - MySQL服务器。你需要该选项，除非你只想连接运行在另一台机器上的MySQL服务器。
- **MySQL-client** - MySQL 客户端程序，用于连接并操作Mysql服务器。

Mysql安装成功后，默认的root用户密码为空，你可以使用以下命令来创建root用户的密码：

```shell
[root@host]# mysqladmin -u root password "new_password";
```

现在你可以通过以下命令来连接到Mysql服务器：

```shell
[root@host]# mysql -u root -p
Enter password:*******
```

# MySQL 管理

# MySQL 连接

以下是从命令行中连接mysql服务器的简单实例：

```shell
[root@host]# mysql -u root -p
Enter password:******
```

退出 mysql> 命令提示窗口可以使用 exit 命令，如下所示：

```sql
mysql> exit
Bye
```

# MySQL 创建数据库

```sql
CREATE DATABASE 数据库名;
```

# MySQL 删除数据库

## drop 命令删除数据库

```sql
drop database <数据库名>;
```

## 使用 mysqladmin 删除数据库

```shell
[root@host]# mysqladmin -u root -p drop RUNOOB
Enter password:******
```

**注意mysqladmin命令的使用**

# MySQL 选择数据库

```sql
[root@host]# mysql -u root -p
Enter password:******
mysql> use RUNOOB;
Database changed
mysql>
```

# MySQL 数据类型

MySQL支持多种类型，大致可以分为三类：数值、日期/时间和字符串(字符)类型。

**注意**：char(n) 和 varchar(n) 中括号中 n 代表字符的个数，并不代表字节个数，比如 CHAR(30) 就可以存储 30 个字符。

# MySQL 创建数据表

以下为创建MySQL数据表的SQL通用语法：

```sql
CREATE TABLE table_name (column_name column_type);
```

# MySQL 删除数据表

以下为删除MySQL数据表的通用语法：

```sql
DROP TABLE table_name ;
```

# MySQL 插入数据

以下为向MySQL数据表插入数据通用的 **INSERT INTO** SQL语法：

```sql
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```

# MySQL 查询数据

## 读取数据表：

```sql
select * from runoob_tbl;
```

# MySQL WHERE 子句

## SQL SELECT WHERE 子句

```sql
SELECT * from runoob_tbl WHERE runoob_author='菜鸟教程';
```

# MySQL UPDATE 更新

## SQL UPDATE 语句：

```sql
mysql> UPDATE runoob_tbl SET runoob_title='学习 C++' WHERE runoob_id=3;
```

# MySQL DELETE 语句

以下是 SQL DELETE 语句从 MySQL 数据表中删除数据的通用语法：

```sql
DELETE FROM table_name [WHERE Clause]
```

# MySQL LIKE 子句

SQL LIKE 子句中使用百分号 **%**字符来表示任意字符，类似于UNIX或正则表达式中的星号 *****。

```sql
mysql> SELECT * from runoob_tbl  WHERE runoob_author LIKE '%COM';
```

# MySQL UNION 操作符

MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。多个 SELECT 语句会删除重复的数据。

## SQL UNION 实例

下面的 SQL 语句从 "Websites" 和 "apps" 表中选取所有**不同的**country（只有不同的值）：

```sql
SELECT country FROM Websites
UNION
SELECT country FROM apps
ORDER BY country;
```

## SQL UNION ALL 实例

下面的 SQL 语句使用 UNION ALL 从 "Websites" 和 "apps" 表中选取**所有的**country（也有重复的值）：

```sql
SELECT country FROM Websites
UNION ALL
SELECT country FROM apps
ORDER BY country;
```

# MySQL 排序

尝试以下实例，结果将按升序及降序排列。

```sql
mysql> SELECT * from runoob_tbl ORDER BY submission_date ASC;
+-----------+---------------+---------------+-----------------+
| runoob_id | runoob_title  | runoob_author | submission_date |
+-----------+---------------+---------------+-----------------+
| 3         | 学习 Java   | RUNOOB.COM    | 2015-05-01      |
| 4         | 学习 Python | RUNOOB.COM    | 2016-03-06      |
| 1         | 学习 PHP    | 菜鸟教程  | 2017-04-12      |
| 2         | 学习 MySQL  | 菜鸟教程  | 2017-04-12      |
+-----------+---------------+---------------+-----------------+
mysql> SELECT * from runoob_tbl ORDER BY submission_date DESC;
+-----------+---------------+---------------+-----------------+
| runoob_id | runoob_title  | runoob_author | submission_date |
+-----------+---------------+---------------+-----------------+
| 1         | 学习 PHP    | 菜鸟教程  | 2017-04-12      |
| 2         | 学习 MySQL  | 菜鸟教程  | 2017-04-12      |
| 4         | 学习 Python | RUNOOB.COM    | 2016-03-06      |
| 3         | 学习 Java   | RUNOOB.COM    | 2015-05-01      |
+-----------+---------------+---------------+-----------------+
```

# MySQL GROUP BY 语句

# MySQL 连接的使用

- **INNER JOIN（内连接,或等值连接）**：获取两个表中字段匹配关系的记录。
- **LEFT JOIN（左连接）：**获取左表所有记录，即使右表没有对应匹配的记录。
- **RIGHT JOIN（右连接）：** 与 LEFT JOIN 相反，用于获取右表所有记录，即使左表没有对应匹配的记录。

# MySQL NULL 值处理

- **IS NULL:** 当列的值是 NULL,此运算符返回 true。
- **IS NOT NULL:** 当列的值不为 NULL, 运算符返回 true。
- **<=>:** 比较操作符（不同于 = 运算符），当比较的的两个值相等或者都为 NULL 时返回 true。

```sql
mysql> SELECT * FROM runoob_test_tbl WHERE runoob_count IS NULL;
```

```sql
mysql> SELECT * from runoob_test_tbl WHERE runoob_count IS NOT NULL;
```

# MySQL 正则表达式

![image-20210226154651898](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20210226154651898.png)

MySQL中使用 REGEXP 操作符来进行正则表达式匹配。

查找name字段中以'st'为开头的所有数据：

```sql
mysql> SELECT name FROM person_tbl WHERE name REGEXP '^st';
```

查找name字段中以'ok'为结尾的所有数据：

```sql
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'ok$';
```

查找name字段中包含'mar'字符串的所有数据：

```sql
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'mar';
```

查找name字段中以元音字符开头或以'ok'字符串结尾的所有数据：

```sql
mysql> SELECT name FROM person_tbl WHERE name REGEXP '^[aeiou]|ok$';
```

# MySQL 事务

MySQL 事务主要用于处理操作量大，复杂度高的数据。比如说，在人员管理系统中，你删除一个人员，你既需要删除人员的基本资料，也要删除和该人员相关的信息，如信箱，文章等等，这样，这些数据库操作语句就构成一个事务！

一般来说，事务是必须满足4个条件（ACID）：：原子性（**A**tomicity，或称不可分割性）、一致性（**C**onsistency）、隔离性（**I**solation，又称独立性）、持久性（**D**urability）。

- **原子性：**一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。
- **一致性：**在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。
- **隔离性：**数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。
- **持久性：**事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。

### MYSQL 事务处理主要有两种方法：

1、用 BEGIN, ROLLBACK, COMMIT来实现

- **BEGIN** 开始一个事务
- **ROLLBACK** 事务回滚
- **COMMIT** 事务确认

2、直接用 SET 来改变 MySQL 的自动提交模式:

- **SET AUTOCOMMIT=0** 禁止自动提交
- **SET AUTOCOMMIT=1** 开启自动提交

```sql
mysql> use RUNOOB;
Database changed
mysql> CREATE TABLE runoob_transaction_test( id int(5)) engine=innodb;  # 创建数据表
Query OK, 0 rows affected (0.04 sec)
 
mysql> select * from runoob_transaction_test;
Empty set (0.01 sec)
 
mysql> begin;  # 开始事务
Query OK, 0 rows affected (0.00 sec)
 
mysql> insert into runoob_transaction_test value(5);
Query OK, 1 rows affected (0.01 sec)
 
mysql> insert into runoob_transaction_test value(6);
Query OK, 1 rows affected (0.00 sec)
 
mysql> commit; # 提交事务
Query OK, 0 rows affected (0.01 sec)
 
mysql>  select * from runoob_transaction_test;
+------+
| id   |
+------+
| 5    |
| 6    |
+------+
2 rows in set (0.01 sec)
 
mysql> begin;    # 开始事务
Query OK, 0 rows affected (0.00 sec)
 
mysql>  insert into runoob_transaction_test values(7);
Query OK, 1 rows affected (0.00 sec)
 
mysql> rollback;   # 回滚
Query OK, 0 rows affected (0.00 sec)
 
mysql>   select * from runoob_transaction_test;   # 因为回滚所以数据没有插入
+------+
| id   |
+------+
| 5    |
| 6    |
+------+
2 rows in set (0.01 sec)
 
mysql>
```

# MySQL ALTER命令

当我们需要修改数据表名或者修改数据表字段时，就需要使用到MySQL ALTER命令。

# MySQL 索引

# MySQL 临时表

```sql
mysql> CREATE TEMPORARY TABLE SalesSummary (
    -> product_name VARCHAR(50) NOT NULL
    -> , total_sales DECIMAL(12,2) NOT NULL DEFAULT 0.00
    -> , avg_unit_price DECIMAL(7,2) NOT NULL DEFAULT 0.00
    -> , total_units_sold INT UNSIGNED NOT NULL DEFAULT 0
);
Query OK, 0 rows affected (0.00 sec)

mysql> INSERT INTO SalesSummary
    -> (product_name, total_sales, avg_unit_price, total_units_sold)
    -> VALUES
    -> ('cucumber', 100.25, 90, 2);

mysql> SELECT * FROM SalesSummary;
+--------------+-------------+----------------+------------------+
| product_name | total_sales | avg_unit_price | total_units_sold |
+--------------+-------------+----------------+------------------+
| cucumber     |      100.25 |          90.00 |                2 |
+--------------+-------------+----------------+------------------+
1 row in set (0.00 sec)
```

# MySQL 复制表

# MySQL 元数据

## 获取服务器元数据

|        命令        |           描述            |
| :----------------: | :-----------------------: |
| SELECT VERSION( )  |      服务器版本信息       |
| SELECT DATABASE( ) | 当前数据库名 (或者返回空) |
|   SELECT USER( )   |        当前用户名         |
|    SHOW STATUS     |        服务器状态         |
|   SHOW VARIABLES   |      服务器配置变量       |

# MySQL 序列使用

# MySQL 运算符

```sql
mysql> select 1+2;
+-----+
| 1+2 |
+-----+
|   3 |
+-----+
```

## 比较运算符

SELECT 语句中的条件语句经常要使用比较运算符。通过这些比较运算符，可以判断表中的哪些记录是符合条件的。比较结果为真，则返回 1，为假则返回 0，比较结果不确定则返回 NULL。

不等于

```sql
mysql> select 2<>3;
+------+
| 2<>3 |
+------+
|    1 |
+------+
```

# 其它类型的数据库

mongodb、redis等等。

| mysql  | mongodb |
| :----: | :-----: |
| 数据库 | 数据库  |
|   表   |  集合   |
|   行   |  文档   |

# 存储过程 procedure

类似于编程语言中的函数或者方法

# 触发器 trigger

一类特殊的存储过程，类似监听器

# 视图 view

由一张表或多个表构成的虚拟表

# 索引 index

就是用来提高数据库查询的效率的，数据结构为B+树

# 事务 transaction

客户端---》连接缓存---》数据库文件

# 数据库设计
