# GROUP BY 子句 #

----------

SQL **GROUP BY** 子句与 SELECT 语句结合在一起使用，可以将相同数据分成一组。

在 SELECT 语句中，GROUP BY 子句紧随 WHERE 子句，在 ORDER BY 子句之前。

## 语法： ##

GROUP BY 子句的基本语法如下所示。GROUP BY 子句必须在 WHERE 子句的条件之后，ORDER BY 子句（如果有的话）之前。

	SELECT column1, column2
	FROM table_name
	WHERE [ conditions ]
	GROUP BY column1, column2
	ORDER BY column1, column2

## 示例： ##

考虑含有如下所示记录的 CUSTOMERS 表：

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

如果你想要知道每个客户的薪水如何，可以写一个带有 GROUP BY 子句的查询：

	SQL> SELECT NAME, SUM(SALARY) FROM CUSTOMERS
	     GROUP BY NAME;

结果如下所示：

	+----------+-------------+
	| NAME     | SUM(SALARY) |
	+----------+-------------+
	| Chaitali |     6500.00 |
	| Hardik   |     8500.00 |
	| kaushik  |     2000.00 |
	| Khilan   |     1500.00 |
	| Komal    |     4500.00 |
	| Muffy    |    10000.00 |
	| Ramesh   |     2000.00 |
	+----------+-------------+

现在，让我们换一张 CUSTOMERS 表，表中记录的 NAME 字段有重复值：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  2 | Ramesh   |  25 | Delhi     |  1500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  4 | kaushik  |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	|  6 | Komal    |  22 | MP        |  4500.00 |
	|  7 | Muffy    |  24 | Indore    | 10000.00 |
	+----+----------+-----+-----------+----------+

同样，如果你想要知道每个客户的薪水如何的话，可以写一个带有 GROUP BY 子句的查询：

	SQL> SELECT NAME, SUM(SALARY) FROM CUSTOMERS
	     GROUP BY NAME;

结果如下所示：

	+---------+-------------+
	| NAME    | SUM(SALARY) |
	+---------+-------------+
	| Hardik  |     8500.00 |
	| kaushik |     8500.00 |
	| Komal   |     4500.00 |
	| Muffy   |    10000.00 |
	| Ramesh  |     3500.00 |
	+---------+-------------+
