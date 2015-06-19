# 全连接 #

**全连接**将左连接和右连接的结果组合在一起。

## 语法： ##

**全连接**的基本语法如下所受：

	SELECT table1.column1, table2.column2...
	FROM table1
	FULL JOIN table2
	ON table1.common_field = table2.common_field;

这里，给出的条件可以是任何根据你的需要写出的条件。

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

现在让我们用全连接将两个表连接在一起：

	SQL> SELECT  ID, NAME, AMOUNT, DATE
	     FROM CUSTOMERS
	     FULL JOIN ORDERS
	     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;

上述语句将会产生如下结果：

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

如果你所用的数据库不支持全连接，比如 MySQL，那么你可以使用 UNION ALL子句来将左连接和右连接结果组合在一起：

	SQL> SELECT  ID, NAME, AMOUNT, DATE
	     FROM CUSTOMERS
	     LEFT JOIN ORDERS
	     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
	UNION ALL
	     SELECT  ID, NAME, AMOUNT, DATE
	     FROM CUSTOMERS
	     RIGHT JOIN ORDERS
	     ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
