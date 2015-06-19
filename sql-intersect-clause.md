# INTERSECT 子句 #

**INTERSECT 子句/运算符**用于将两个 SELECT 语句结合在一起，只返回第一个 SELECT 语句的结果中与第二个 SELECT 语句的结果中的记录完全相同的那些记录。这就意味着，INTERSECT 仅返回两个 SELECT 子句的共同结果。

INTERSECT 运算符遵循同 UNION 运算符一样规则。MySQL 不支持 INTERSECT 运算符。

## 语法： ##

**INTERSECT**子句的基本语法如下所示：

	SELECT column1 [, column2 ]
	FROM table1 [, table2 ]
	[WHERE condition]
	
	INTERSECT
	
	SELECT column1 [, column2 ]
	FROM table1 [, table2 ]
	[WHERE condition]

这里给定的条件可以是任何根据你自己的需要而得出的表达式。

## 示例： ##

考虑如下两个表格，（a）CUSTOMERS 表：

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

（b）ORDERS 表：

	+-----+---------------------+-------------+--------+
	| OID | DATE                |          ID | AMOUNT |
	+-----+---------------------+-------------+--------+
	| 102 | 2009-10-08 00:00:00 |           3 |   3000 |
	| 100 | 2009-10-08 00:00:00 |           3 |   1500 |
	| 101 | 2009-11-20 00:00:00 |           2 |   1560 |
	| 103 | 2008-05-20 00:00:00 |           4 |   2060 |
	+-----+---------------------+-------------+--------+

现在，让我将这两个表的 SELECT 查询的结果结合在一起：

	SQL> SELECT  ID, NAME, AMOUNT, DATE
	     FROM CUSTOMERS
	     LEFT JOIN ORDERS
	     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
	INTERSECT
	     SELECT  ID, NAME, AMOUNT, DATE
	     FROM CUSTOMERS
	     RIGHT JOIN ORDERS
	     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;

其结果如下所示：

	+------+---------+--------+---------------------+
	| ID   | NAME    | AMOUNT | DATE                |
	+------+---------+--------+---------------------+
	|    3 | kaushik |   3000 | 2009-10-08 00:00:00 |
	|    3 | kaushik |   1500 | 2009-10-08 00:00:00 |
	|    2 | Ramesh  |   1560 | 2009-11-20 00:00:00 |
	|    4 | kaushik |   2060 | 2008-05-20 00:00:00 |
	+------+---------+--------+---------------------+

