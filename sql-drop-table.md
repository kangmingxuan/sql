# 删除表 #

----------

SQL **DROP TABLE** 语句用于移除表定义以及表中所有的数据、索引、触发器、约束和权限设置。

**注意：**使用此命令应当特别小心，因为数据表一旦被删除，表中所有的信息就会永久丢失。

## 语法： ##

DROP TABLE 语句的基本语法如下所示：

    DROP TABLE table_name;

## 示例： ##

先确认操作的是 CUSTOMERS 表，才能将其从数据库中删除：

    SQL> DESC CUSTOMERS;
    +---------+---------------+------+-----+---------+-------+
    | Field   | Type          | Null | Key | Default | Extra |
    +---------+---------------+------+-----+---------+-------+
    | ID      | int(11)       | NO   | PRI |         |       |
    | NAME    | varchar(20)   | NO   |     |         |       |
    | AGE     | int(11)       | NO   |     |         |       |
    | ADDRESS | char(25)      | YES  |     | NULL    |       |
    | SALARY  | decimal(18,2) | YES  |     | NULL    |       |
    +---------+---------------+------+-----+---------+-------+
    5 rows in set (0.00 sec)

返回结果表明 CUSTOMERS 表在数据库中，接着让我们用下面的命令删除它：

    SQL> DROP TABLE CUSTOMERS;
    Query OK, 0 rows affected (0.01 sec)

现在，如果你再用 DESC 命令的话，会得到如下所示的错误信息：

    SQL> DESC CUSTOMERS;
    ERROR 1146 (42S02): Table 'TEST.CUSTOMERS' doesn't exist

这里，TEST 是示例所用的数据库的名称。
