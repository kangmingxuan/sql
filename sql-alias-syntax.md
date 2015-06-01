# 别名 #

----------

我们可以使用**别名（Alias）**来对数据表或者列进行临时命名。

使用别名意味着要用特定的 SQL 语句对表进行重命名。重命名是临时的，数据库中表的实际名字并不会改变。

对于特定的 SQL 查询，需要使用列别名来对表中的列进行重命名。

## 语法： ##

**表别名**的基本语法如下：

	SELECT column1, column2....
	FROM table_name AS alias_name
	WHERE [condition];

**列别名**的基本语法如下：

	SELECT column_name AS alias_name
	FROM table_name
	WHERE [condition];

## 示例： ##

考虑下面两个数据表，（a）CUSTOMERS 表，如下：

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

（b）另一个是ORDERS表，如下所示：

	+-----+---------------------+-------------+--------+
	|OID  | DATE                | CUSTOMER_ID | AMOUNT |
	+-----+---------------------+-------------+--------+
	| 102 | 2009-10-08 00:00:00 |           3 |   3000 |
	| 100 | 2009-10-08 00:00:00 |           3 |   1500 |
	| 101 | 2009-11-20 00:00:00 |           2 |   1560 |
	| 103 | 2008-05-20 00:00:00 |           4 |   2060 |
	+-----+---------------------+-------------+--------+

下面是**表别名**的用法：

	SQL> SELECT C.ID, C.NAME, C.AGE, O.AMOUNT 
	        FROM CUSTOMERS AS C, ORDERS AS O
	        WHERE  C.ID = O.CUSTOMER_ID;

上面语句的运行结果如下所示：

	+----+----------+-----+--------+
	| ID | NAME     | AGE | AMOUNT |
	+----+----------+-----+--------+
	|  3 | kaushik  |  23 |   3000 |
	|  3 | kaushik  |  23 |   1500 |
	|  2 | Khilan   |  25 |   1560 |
	|  4 | Chaitali |  25 |   2060 |
	+----+----------+-----+--------+

下面是**列别名**的用法：

	SQL> SELECT  ID AS CUSTOMER_ID, NAME AS CUSTOMER_NAME
	     FROM CUSTOMERS
	     WHERE SALARY IS NOT NULL;

其运行结果如下所示：

	+-------------+---------------+
	| CUSTOMER_ID | CUSTOMER_NAME |
	+-------------+---------------+
	|           1 | Ramesh        |
	|           2 | Khilan        |
	|           3 | kaushik       |
	|           4 | Chaitali      |
	|           5 | Hardik        |
	|           6 | Komal         |
	|           7 | Muffy         |
	+-------------+---------------+
