# UPDATE 语句 #

----------

SQL **UPDATE** 语句用于修改表中现有的记录。

你可以在 UPDATE 语句中使用 WHERE 子句来修改选定的记录，否则所有记录都会收到影响。

## 语法： ##

带 WHERE 子句的 UPDATE 语句的基本语法如下：

    UPDATE table_name
    SET column1 = value1, column2 = value2...., columnN = valueN
    WHERE [condition];

WHERE 子句中，你可以将 N　个条件用　AND 或者 OR 连接在一起。

## 例子： ##

考虑 CUSTOMERS 表，表中记录如下所示：

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

下例将会更新 ID 为 6 的客户的 ADDRESS 字段：

    SQL> UPDATE CUSTOMERS
    SET ADDRESS = 'Pune'
    WHERE ID = 6;

更新之后，表中的记录如下所示：

    +----+----------+-----+-----------+----------+
    | ID | NAME     | AGE | ADDRESS   | SALARY   |
    +----+----------+-----+-----------+----------+
    |  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
    |  2 | Khilan   |  25 | Delhi     |  1500.00 |
    |  3 | kaushik  |  23 | Kota      |  2000.00 |
    |  4 | Chaitali |  25 | Mumbai    |  6500.00 |
    |  5 | Hardik   |  27 | Bhopal    |  8500.00 |
    |  6 | Komal    |  22 | Pune      |  4500.00 |
    |  7 | Muffy    |  24 | Indore    | 10000.00 |
    +----+----------+-----+-----------+----------+

如果你想要修改 CUSTOMERS 表中所有记录的 ADDRESS 和 SALARY 字段，只要把 WHERE 子句去掉即可。此时，UPDATE 语句如下所示：

    SQL> UPDATE CUSTOMERS
    SET ADDRESS = 'Pune', SALARY = 1000.00;

上述语句执行后， CUSTOMERS 表中的记录如下：

    +----+----------+-----+---------+---------+
    | ID | NAME     | AGE | ADDRESS | SALARY  |
    +----+----------+-----+---------+---------+
    |  1 | Ramesh   |  32 | Pune    | 1000.00 |
    |  2 | Khilan   |  25 | Pune    | 1000.00 |
    |  3 | kaushik  |  23 | Pune    | 1000.00 |
    |  4 | Chaitali |  25 | Pune    | 1000.00 |
    |  5 | Hardik   |  27 | Pune    | 1000.00 |
    |  6 | Komal    |  22 | Pune    | 1000.00 |
    |  7 | Muffy    |  24 | Pune    | 1000.00 |
    +----+----------+-----+---------+---------+
