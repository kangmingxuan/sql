# TRUNCATE TABLE 命令 #

----------

SQL **TRUNCATE TABLE** 命令用于删除现有数据表中的所有数据。

你也可以使用 DROP TABLE 命令来删除整个数据表，不过 DROP TABLE 命令不但会删除表中所有数据，还会将整个表结构从数据库中移除。如果想要重新向表中存储数据的话，必须重建该数据表。

## 语法： ##

**TRUNCATE TABLE** 的基本语法如下所示：

	TRUNCATE TABLE  table_name;

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

下面的示例展示了 TRUNCATE 命令的用法：

	TRUNCATE TABLE CUSTOMERS;

现在，CUSTOMERS 表已经被清空了，SELECT 语句的输出应当如下所示：

	SQL> SELECT * FROM CUSTOMERS;
	Empty set (0.00 sec)
