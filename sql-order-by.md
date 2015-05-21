# ORDER BY 子句 #

----------

SQL **ORDER BY** 子句根据一列或者多列的值，按照升序或者降序排列数据。某些数据库默认以升序排列查询结果。

## 语法： ##

ORDER BY 子句的基本语法如下所示：

	SELECT column-list 
	FROM table_name 
	[WHERE condition] 
	[ORDER BY column1, column2, .. columnN] [ASC | DESC];

ORDER BY 子句可以同时使用多个列作为排序条件。无论用哪一列作为排序条件，都要确保该列在存在。

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

下面的例子将查询结果按照 NAME 和 SALARY 升序排列：

	SQL> SELECT * FROM CUSTOMERS
	     ORDER BY NAME, SALARY;

结果如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  6 | Komal    |  22 | MP        |  4500.00 |
	|  7 | Muffy    |  24 | Indore    | 10000.00 |
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	+----+----------+-----+-----------+----------+

下面的例子将查询结果按照 NAME 降序排列：

	SQL> SELECT * FROM CUSTOMERS
	     ORDER BY NAME DESC;

结果如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  7 | Muffy    |  24 | Indore    | 10000.00 |
	|  6 | Komal    |  22 | MP        |  4500.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	+----+----------+-----+-----------+----------+
