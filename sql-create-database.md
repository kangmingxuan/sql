# 创建数据库 #

SQL **CREATE DATABASE** 语句用于创建新的 SQL 数据库。

## 语法： ##

CREATE DATABASE 的基本语法如下所示：

    CREATE DATABASE DatabaseName;

在 RDBMS 中，数据库的名字应该是唯一的。

## 示例： ##

如果你先想要创建一个新数据库<testDB>，那么 CREATE DATABASE 语句应该这么写：

    SQL> CREATE DATABASE testDB;

创建数据库之前，请确保你有管理员权限。数据库一旦创建成功就会出现在数据库列表中。

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
    | testDB             |
    +--------------------+
    7 rows in set (0.00 sec)
