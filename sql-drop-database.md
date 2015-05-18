# 删除数据库 #

SQL **DROP DATABASE** 语句用于删除现存的数据库。

## 语法： ##

DROP DATABASE 的基本语法如下：

    DROP DATABASE DatabaseName;

无论任何时候，RDBMS 中数据库的名字都应该是唯一的。

## 示例： ##

如果你想要删除数据库<testDB>，那么 DROP DATABASE 语句应该这么写：

    SQL> DROP DATABASE testDB;

**注意：**执行数据库删除操作应当十分谨慎，因为数据库一旦删除，存储的所有数据都会丢失。

删除任何数据库之前，请确保你有管理员权限。数据库删除之后，你可以在数据库列表中看到变化：

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
