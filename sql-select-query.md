# SELECT 语句 #

----------

SQL **SELECT** 语句用于从数据库的表中取回所需的数据，并以表的形式返回。返回的表被称作结果集。

## 语法： ##

SELECT 语句的基本语法如下：

    SELECT column1, column2, columnN FROM table_name;

这里，column1, column2...是你想要从表中取回的字段。如果要取回表中所有字段的话，可以使用下面的语法：

    SELECT * FROM table_name;

## 示例： ##

考虑 CUSTOMERS 表，该表包含的记录如下所示：

    +----+----------+-----+-----------+----------+
    | ID | NAME     | AGE | ADDRESS   | SALARY   |
    +----+----------+-----+-----------+----------+
    |  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
    |  2 | Khilan   |  25 | Delhi     |  1500.00 |
    |  3 | kaushik  |  23 | Kota      |  2000.00 |
    |  4 | Chaitali |  25 | Mumbai    |  6500.00 |
    |  5 | Hardik   |  27 | Bhopal    |  8500.00 |
    |  6 | Komal    |  22 | MP        |  4500.00 |
    |  7 | Muffy    |  24 | Indore    | 10000.00 |
    +----+----------+-----+-----------+----------+

下面的例子将从 CUSTOMERS 表中获取客户的 ID、Name 和 Salary 字段：

    SQL> SELECT ID, NAME, SALARY FROM CUSTOMERS;

运行结果如下所示：

    +----+----------+----------+
    | ID | NAME     | SALARY   |
    +----+----------+----------+
    |  1 | Ramesh   |  2000.00 |
    |  2 | Khilan   |  1500.00 |
    |  3 | kaushik  |  2000.00 |
    |  4 | Chaitali |  6500.00 |
    |  5 | Hardik   |  8500.00 |
    |  6 | Komal    |  4500.00 |
    |  7 | Muffy    | 10000.00 |
    +----+----------+----------+

如果想要取回 CUSTOMERS 表中所有的字段的话，SQL 查询应该这么写：

    SQL> SELECT * FROM CUSTOMERS;

运行结果如下所示：

    +----+----------+-----+-----------+----------+
    | ID | NAME     | AGE | ADDRESS   | SALARY   |
    +----+----------+-----+-----------+----------+
    |  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
    |  2 | Khilan   |  25 | Delhi     |  1500.00 |
    |  3 | kaushik  |  23 | Kota      |  2000.00 |
    |  4 | Chaitali |  25 | Mumbai    |  6500.00 |
    |  5 | Hardik   |  27 | Bhopal    |  8500.00 |
    |  6 | Komal    |  22 | MP        |  4500.00 |
    |  7 | Muffy    |  24 | Indore    | 10000.00 |
    +----+----------+-----+-----------+----------+

