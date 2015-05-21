# WHERE 子句 #

----------

SQL **WHERE** 子句用于有条件地从单个表中取回数据或者将多个表进行合并。

如果条件满足，则查询只返回表中满足条件的值。你可以用 WHERE 子句来过滤查询结果，只获取必要的记录。

WHERE 子句不仅可以用于 SELECT 语句，还可以用于 UPDATE、DELETE 等语句，其用法见后面的章节。

## 语法： ##

在 SELECT 语句中使用 WHERE 子句的基本句法如下：

    SELECT column1, column2, columnN 
    FROM table_name
    WHERE [condition]

在指定条件时，可以使用关系运算符和逻辑运算符，例如 >、<、=、LIKE、NOT 等。

## 示例 ##

考虑 CUSTOMERS 表，表中含有如下所示的记录：

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

下面的示例将从 CUSTOMERS 表中选取 Salary 字段的值大于 2000 的所有记录，并返回这些记录的 ID、Name、Salary 三个字段。

    SQL> SELECT ID, NAME, SALARY 
    FROM CUSTOMERS
    WHERE SALARY > 2000;

运行结果如下所示：

    +----+----------+----------+
    | ID | NAME     | SALARY   |
    +----+----------+----------+
    |  4 | Chaitali |  6500.00 |
    |  5 | Hardik   |  8500.00 |
    |  6 | Komal    |  4500.00 |
    |  7 | Muffy    | 10000.00 |
    +----+----------+----------+

下面的示例将从 CUSTOMERS 表中选取名字为 Hardik 的客户的记录，并返回其 ID、Name 和 Salary 三个字段。这里值得注意的是，所有的字符串都必须写在单引号中，就像上面的例子中所有的数值都不能放在引号中一样。

    SQL> SELECT ID, NAME, SALARY 
    FROM CUSTOMERS
    WHERE NAME = 'Hardik';

结果如下所示：

    +----+----------+----------+
    | ID | NAME     | SALARY   |
    +----+----------+----------+
    |  5 | Hardik   |  8500.00 |
    +----+----------+----------+
