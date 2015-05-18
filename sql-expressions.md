# 表达式 #

----------

表达式是一个或者多个值、运算符和 SQL 函数的组合。每个表达式都有值，通过求值可以得到。

SQL 表达式看起来就像数学公式一样，它们以查询语言写就。你也可以用它们在数据库中查询符合特定条件的数据。

## 语法： ##

考虑如下所示的 SELECT 语句的基本语法：

    SELECT column1, column2, columnN 
    FROM table_name 
    WHERE [CONDITION|EXPRESSION];

SQL 表达式有很多种不同的类型，如下所示：


### 布尔表达式 ###

SQL 布尔表达式以单值条件检索数据，其语法如下：

    SELECT column1, column2, columnN 
    FROM table_name 
    WHERE SINGLE VALUE MATCHTING EXPRESSION;

考虑如下所示的客户信息表：

    SQL> SELECT * FROM CUSTOMERS;
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
    7 rows in set (0.00 sec)

下面是一个展示 SQL 布尔表达式的简单例子：

    SQL> SELECT * FROM CUSTOMERS WHERE SALARY = 10000;
    +----+-------+-----+---------+----------+
    | ID | NAME  | AGE | ADDRESS | SALARY   |
    +----+-------+-----+---------+----------+
    |  7 | Muffy |  24 | Indore  | 10000.00 |
    +----+-------+-----+---------+----------+
    1 row in set (0.00 sec)

### 数值表达式 ###

数值表达式用于在查询中执行数学运算。其语法如下：

    SELECT numerical_expression as  OPERATION_NAME
    [FROM table_name
    WHERE CONDITION] ;

这里  numerical_expression 为数学运算或者任何公式。下面是一个说明 SQL 数值表达式用法的简单例子：

    SQL> SELECT (15 + 6) AS ADDITION
    +----------+
    | ADDITION |
    +----------+
    |       21 |
    +----------+
    1 row in set (0.00 sec)

SQL 有一系列的内建函数，例如 avg()、sum()、count() 等，这些函数用于在表上或者表中的特定列上执行聚合数据运算。

    SQL> SELECT COUNT(*) AS "RECORDS" FROM CUSTOMERS; 
    +---------+
    | RECORDS |
    +---------+
    |       7 |
    +---------+
    1 row in set (0.00 sec)

### 时间表达式 ###

时间表达式返回当前系统的日期和时间：

    SQL>  SELECT CURRENT_TIMESTAMP;
    +---------------------+
    | Current_Timestamp   |
    +---------------------+
    | 2009-11-12 06:40:23 |
    +---------------------+
    1 row in set (0.00 sec)

下面是一个日期表达式：

    SQL>  SELECT  GETDATE();;
    +-------------------------+
    | GETDATE                 |
    +-------------------------+
    | 2009-10-22 12:07:18.140 |
    +-------------------------+
    1 row in set (0.00 sec)
