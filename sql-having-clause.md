# HAVING 子句 #

----------

HAVING 子句使你能够指定过滤条件，从而控制查询结果中哪些组可以出现在最终结果里面。

WHERE 子句对被选择的列施加条件，而 HAVING 子句则对 GROUP BY 子句所产生的组施加条件。

## 语法： ##

下面可以看到 HAVING 子句在 SELECT 查询中的位置：

	SELECT
	FROM
	WHERE
	GROUP BY
	HAVING
	ORDER BY

在 SELECT 查询中，HAVING 子句必须紧随 GROUP BY 子句，并出现在 ORDER BY 子句（如果有的话）之前。带有 HAVING 子句的 SELECT 语句的语法如下所示：

	SELECT column1, column2
	FROM table1, table2
	WHERE [ conditions ]
	GROUP BY column1, column2
	HAVING [ conditions ]
	ORDER BY column1, column2

## 示例： ##

考虑 CUSTOMERS 表，表中的记录如下所示：

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

下面是一个有关 HAVING 子句使用的实例，该实例将会筛选出出现次数大于或等于 2 的所有记录。

	SQL > SELECT ID, NAME, AGE, ADDRESS, SALARY
	FROM CUSTOMERS
	GROUP BY age
	HAVING COUNT(age) >= 2;

其执行结果如下所示：

	+----+--------+-----+---------+---------+
	| ID | NAME   | AGE | ADDRESS | SALARY  |
	+----+--------+-----+---------+---------+
	|  2 | Khilan |  25 | Delhi   | 1500.00 |
	+----+--------+-----+---------+---------+

