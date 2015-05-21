# 选择数据库，USE 语句 #

----------

如果你的数据库架构中有多个数据库同时存在，那么在开始操作之前必须先选定其中一个。

SQL **USE** 语句用于选取当前数据库架构中存在的任一数据库。

## 语法： ##

USE 语句的基本语法如下：

    USE DatabaseName;

再次强调，RDBMS 中数据库的名字应该唯一。

## 示例： ##

按照以下方式查看所有可用的数据库：

    SQL> SHOW DATABASES;
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | AMROOD             |
    | TUTORIALSPOINT     |
    | mysql              |
    | orig               |
    | test               |
    +--------------------+
    6 rows in set (0.00 sec)

如果你想要操作 AMROOD 数据库的话，可以执行下面的 SQL 命令选中它，然后开始执行你所需要的操作。

    SQL> USE AMROOD;
