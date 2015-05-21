# AND 和 OR 连接运算符 #

----------

SQL **AND** 和 **OR** 运算符可以将多个条件结合在一起，从而过滤 SQL 语句的返回结果。这两个运算符被称作连接运算符。

## AND 运算符： ##

AND 运算符使得 SQL 语句的 WHERE 子句中可以同时存在多个条件。

## 语法： ##

在 WHERE 子句中使用 AND 运算符的基本语法如下：

    SELECT column1, column2, columnN 
    FROM table_name
    WHERE [condition1] AND [condition2]...AND [conditionN];

你可以将 N 个条件用 AND 运算符结合在一起。对于 SQL 语句要执行的动作来说——无论是事务还是查询，AND 运算符连接的所有条件都必须为 TRUE。

## 示例： ##

考虑如下所示的 CUSTOMERS 表：

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

下面的示例将从 CUSTOMERS 表中选取所有 Salary 大于 2000 且 Age 小于 25 的记录，并返回其 ID、Name 和 Salary 字段。

    SQL> SELECT ID, NAME, SALARY 
    FROM CUSTOMERS
    WHERE SALARY > 2000 AND age < 25;

结果如下所示：

    +----+-------+----------+
    | ID | NAME  | SALARY   |
    +----+-------+----------+
    |  6 | Komal |  4500.00 |
    |  7 | Muffy | 10000.00 |
    +----+-------+----------+

## OR 运算符： ##

OR 运算符用于将 SQL 语句中 WHERE  子句的多个条件结合起来。

## 语法： ##

在 WHERE 子句中使用 OR 运算符的基本语法如下：

    SELECT column1, column2, columnN 
    FROM table_name
    WHERE [condition1] OR [condition2]...OR [conditionN]

你可以将 N 个条件用 OR 运算符结合在一起。对于 SQL 语句要执行的动作来说——无论是事务还是查询，OR 运算符连接的所有条件中只需要有一个为 TRUE 即可。

## 示例： ##

考虑如下所示的 CUSTOMERS 表：

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

下面的示例将从 CUSTOMERS 表中选取所有 Salary 大于 2000 或 Age 小于 25 的记录，并返回其 ID、Name 和 Salary 字段。

    SQL> SELECT ID, NAME, SALARY 
    FROM CUSTOMERS
    WHERE SALARY > 2000 OR age < 25;

结果如下所示：

    +----+----------+----------+
    | ID | NAME     | SALARY   |
    +----+----------+----------+
    |  3 | kaushik  |  2000.00 |
    |  4 | Chaitali |  6500.00 |
    |  5 | Hardik   |  8500.00 |
    |  6 | Komal    |  4500.00 |
    |  7 | Muffy    | 10000.00 |
    +----+----------+----------+
