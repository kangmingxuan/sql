# UNION 子句 #

----------

SQL **UNION** 子句/运算符用于将两个或者更多的 SELECT 语句的运算结果组合起来。

在使用 UNION 的时候，每个 SELECT 语句必须有相同数量的选中列、相同数量的列表达式、相同的数据类型，并且它们出现的次序要一致，不过长度不一定要相同。

## 语法： ##

**UNION** 子句的基本语法如下所示：

	SELECT column1 [, column2 ]
	FROM table1 [, table2 ]
	[WHERE condition]
	
	UNION
	
	SELECT column1 [, column2 ]
	FROM table1 [, table2 ]
	[WHERE condition]

这里的条件可以是任何根据你的需要而设的条件。

## 示例： ##

考虑如下两张表，（a）CUSTOMERS表：

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

（b）另一张表是 ORDERS 表，如下所示：

	+-----+---------------------+-------------+--------+
	|OID  | DATE                | CUSTOMER_ID | AMOUNT |
	+-----+---------------------+-------------+--------+
	| 102 | 2009-10-08 00:00:00 |           3 |   3000 |
	| 100 | 2009-10-08 00:00:00 |           3 |   1500 |
	| 101 | 2009-11-20 00:00:00 |           2 |   1560 |
	| 103 | 2008-05-20 00:00:00 |           4 |   2060 |
	+-----+---------------------+-------------+--------+

现在，让我们用 SELECT 语句将这两张表连接起来：

	SQL> SELECT  ID, NAME, AMOUNT, DATE
	     FROM CUSTOMERS
	     LEFT JOIN ORDERS
	     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
	UNION
	     SELECT  ID, NAME, AMOUNT, DATE
	     FROM CUSTOMERS
	     RIGHT JOIN ORDERS
	     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;

结果如下所示：

	+------+----------+--------+---------------------+
	| ID   | NAME     | AMOUNT | DATE                |
	+------+----------+--------+---------------------+
	|    1 | Ramesh   |   NULL | NULL                |
	|    2 | Khilan   |   1560 | 2009-11-20 00:00:00 |
	|    3 | kaushik  |   3000 | 2009-10-08 00:00:00 |
	|    3 | kaushik  |   1500 | 2009-10-08 00:00:00 |
	|    4 | Chaitali |   2060 | 2008-05-20 00:00:00 |
	|    5 | Hardik   |   NULL | NULL                |
	|    6 | Komal    |   NULL | NULL                |
	|    7 | Muffy    |   NULL | NULL                |
	+------+----------+--------+---------------------+

## UNION ALL 子句： ##

UNION ALL 运算符用于将两个 SELECT 语句的结果组合在一起，重复行也包含在内。

UNION ALL 运算符所遵从的规则与 UNION 一致。

## 语法： ##

**UNION ALL**的基本语法如下：

	SELECT column1 [, column2 ]
	FROM table1 [, table2 ]
	[WHERE condition]
	
	UNION ALL
	
	SELECT column1 [, column2 ]
	FROM table1 [, table2 ]
	[WHERE condition]

## 示例： ##

考虑如下两张表，（a）CUSTOMERS表：

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

（b）另一张表是 ORDERS 表，如下所示：

	+-----+---------------------+-------------+--------+
	|OID  | DATE                | CUSTOMER_ID | AMOUNT |
	+-----+---------------------+-------------+--------+
	| 102 | 2009-10-08 00:00:00 |           3 |   3000 |
	| 100 | 2009-10-08 00:00:00 |           3 |   1500 |
	| 101 | 2009-11-20 00:00:00 |           2 |   1560 |
	| 103 | 2008-05-20 00:00:00 |           4 |   2060 |
	+-----+---------------------+-------------+--------+

结果如下所示：

	+------+----------+--------+---------------------+
	| ID   | NAME     | AMOUNT | DATE                |
	+------+----------+--------+---------------------+
	|    1 | Ramesh   |   NULL | NULL                |
	|    2 | Khilan   |   1560 | 2009-11-20 00:00:00 |
	|    3 | kaushik  |   3000 | 2009-10-08 00:00:00 |
	|    3 | kaushik  |   1500 | 2009-10-08 00:00:00 |
	|    4 | Chaitali |   2060 | 2008-05-20 00:00:00 |
	|    5 | Hardik   |   NULL | NULL                |
	|    6 | Komal    |   NULL | NULL                |
	|    7 | Muffy    |   NULL | NULL                |
	|    3 | kaushik  |   3000 | 2009-10-08 00:00:00 |
	|    3 | kaushik  |   1500 | 2009-10-08 00:00:00 |
	|    2 | Khilan   |   1560 | 2009-11-20 00:00:00 |
	|    4 | Chaitali |   2060 | 2008-05-20 00:00:00 |
	+------+----------+--------+---------------------+

另外，还有两个子句（亦即运算法）与 UNION 子句非常相像：

- [SQL INTERSECT 子句]()：用于组合两个 SELECT 语句，但是只返回两个 SELECT 语句的结果中都有的行。
- [SQL EXCEPT 子句]()：组合两个 SELECT 语句，并将第一个 SELECT 语句的结果中存在，但是第二个 SELECT 语句的结果中不存在的行返回。

