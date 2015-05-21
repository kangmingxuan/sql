# 创建表 #

----------

创建一个基本的表需要做的工作包括：命名表、定义列和各列的数据类型。

SQL 语言使用 **CREATE TABLE** 语句来创建新表。

## 语法： ##

CREATE TABLE 的基本语法如下所示：

    CREATE TABLE table_name(
       column1 datatype,
       column2 datatype,
       column3 datatype,
       .....
       columnN datatype,
       PRIMARY KEY( one or more columns )
    );

CREATE TABLE 向数据库系统指明了你的意图。在此例中，你想要创建一个新表，新表的唯一名称（或者说标识符）紧跟在 CREATE TABLE 后面。

随后的圆括号以列表的形式定义了表中的列以及各列所属的数据类型。下面的示例对该创建新表的语法做出了更清晰的阐释。

> 将 CREATE TABLE 语句和 SELECT 语句结合起来可以创建现有表的副本。详细信息请见[利用现有表创建新表](sql-create-table-using-tables.htm).

## 示例： ##

下面的示例创建了一个 CUSTOMERS 表，主键为 ID，某些字段具有 NOT NULL 的约束，表示在创建新的记录时这些字段不能为 NULL。

    SQL> CREATE TABLE CUSTOMERS(
       ID   INT              NOT NULL,
       NAME VARCHAR (20)     NOT NULL,
       AGE  INT              NOT NULL,
       ADDRESS  CHAR (25) ,
       SALARY   DECIMAL (18, 2),       
       PRIMARY KEY (ID)
    );

你可以通过查看 SQL 服务器返回的消息来确定新表创建成功，或者也可以像下面这样使用 **DESC** 命令：

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

现在数据库中已经有 CUSTOMERS 表了，你可以用它来存储和客户有关的信息。
