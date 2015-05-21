# DISTINCT 关键字 #

----------

SQL **DISTINCT** 关键字同 SELECT 语句一起使用，可以去除所有重复记录，只返回唯一项。

有时候，数据表中可能会有重复的记录。在检索这些记录的时候，应该只取回唯一的记录，而不是重复的。

## 语法： ##

使用 DISTINCT 关键字去除查询结果中的重复记录的基本语法如下所示：

	SELECT DISTINCT column1, column2,.....columnN 
	FROM table_name
	WHERE [condition]

## 示例： ##

考虑含有如下记录的 CUSTOMERS 表：

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

首先，让我们看一下下面的 SELECT 语句是如何返回重复记录的：

	SQL> SELECT SALARY FROM CUSTOMERS
	     ORDER BY SALARY;

上述语句的运行结果如下所示，2000 的薪水出现了两次，表明原表中存在（SALARY字段）重复记录。

	+----------+
	| SALARY   |
	+----------+
	|  1500.00 |
	|  2000.00 |
	|  2000.00 |
	|  4500.00 |
	|  6500.00 |
	|  8500.00 |
	| 10000.00 |
	+----------+

现在，我们在 SELECT 语句中使用 DISTINCT 关键字，然后看有什么样的结果：

	SQL> SELECT DISTINCT SALARY FROM CUSTOMERS
	     ORDER BY SALARY;

这一次结果中就没有重复的条目了：

	+----------+
	| SALARY   |
	+----------+
	|  1500.00 |
	|  2000.00 |
	|  4500.00 |
	|  6500.00 |
	|  8500.00 |
	| 10000.00 |
	+----------+
