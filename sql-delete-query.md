# DELETE 语句 #

----------

SQL **DELETE** 语句用于删除表中现有的记录。

你可以在 DELETE 语句中使用 WHERE 子句来删除选定的记录，否则所有的记录都会被删除。

## 语法： ##

带 WHERE　子句的　DELETE 语句的基本语法如下：

	DELETE FROM table_name
	WHERE [condition];

WHERE　子句中，你可以将　N 个条件用 AND 或者 OR 连接在一起。

## 例子： ##

考虑 CUSTOMERS 表，表中记录如下所示：

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

下面的示例代码将从中**删除** ID 为 6 的客户：

	SQL> DELETE FROM CUSTOMERS
	WHERE ID = 6;

上述代码运行之后，CUSTOMERS 表中的记录如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	|  7 | Muffy    |  24 | Indore    | 10000.00 |
	+----+----------+-----+-----------+----------+

如果你想要删除 CUSTOMERS 表中所有的记录的话，只要将 WHERE 子句去掉即可。此时，DELETE 语句如下所示：

	SQL> DELETE FROM CUSTOMERS;

现在，CUSTOMERS 表中就空空如也了。
