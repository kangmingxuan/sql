# TOP、LIMIT 和 ROWNUM 子句 #

----------

SQL **TOP** 子句用于从一张数据表中取回前 N 个或者 X% 的记录。

**注意：**所有的数据库系统都不支持 TOP 子句。例如，MySQL 支持 **LIMIT** 子句，用以取回有限数量的记录，而 Oracle 则使用 **ROWNUM** 子句来实现这一功能。

## 语法： ##

在　SELECT　语句中使用　TOP　子句的基本语法如下所示：

	SELECT TOP number|percent column_name(s)
	FROM table_name
	WHERE [condition]

## 示例： ##

考虑含有如下所示记录的　CUSTOMERS　表：

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

下面的例子将从　CUSTOMERS　表中取回前　３　条记录：

	SQL> SELECT TOP 3 * FROM CUSTOMERS;

结果如下所示：

	+----+---------+-----+-----------+---------+
	| ID | NAME    | AGE | ADDRESS   | SALARY  |
	+----+---------+-----+-----------+---------+
	|  1 | Ramesh  |  32 | Ahmedabad | 2000.00 |
	|  2 | Khilan  |  25 | Delhi     | 1500.00 |
	|  3 | kaushik |  23 | Kota      | 2000.00 |
	+----+---------+-----+-----------+---------+

如果你在使用　MySQL　数据库服务器，那么等价的例子如下所示：

	SQL> SELECT * FROM CUSTOMERS
	LIMIT 3;

结果如下所示：

	+----+---------+-----+-----------+---------+
	| ID | NAME    | AGE | ADDRESS   | SALARY  |
	+----+---------+-----+-----------+---------+
	|  1 | Ramesh  |  32 | Ahmedabad | 2000.00 |
	|  2 | Khilan  |  25 | Delhi     | 1500.00 |
	|  3 | kaushik |  23 | Kota      | 2000.00 |
	+----+---------+-----+-----------+---------+

如果你在使用　Oracle　数据库服务器，那么等价的例子如下所示：

	SQL> SELECT * FROM CUSTOMERS
	WHERE ROWNUM <= 3;

结果如下所示：

	+----+---------+-----+-----------+---------+
	| ID | NAME    | AGE | ADDRESS   | SALARY  |
	+----+---------+-----+-----------+---------+
	|  1 | Ramesh  |  32 | Ahmedabad | 2000.00 |
	|  2 | Khilan  |  25 | Delhi     | 1500.00 |
	|  3 | kaushik |  23 | Kota      | 2000.00 |
	+----+---------+-----+-----------+---------+
