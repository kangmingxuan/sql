# MAX 函数 #

**MAX**函数用于找出记录集中具有最大值的记录。

要理解 MAX 函数，请考虑 employee_tbl 表，表中记录如下所示：

	SQL> SELECT * FROM employee_tbl;
	+------+------+------------+--------------------+
	| id   | name | work_date  | daily_typing_pages |
	+------+------+------------+--------------------+
	|    1 | John | 2007-01-24 |                250 |
	|    2 | Ram  | 2007-05-27 |                220 |
	|    3 | Jack | 2007-05-06 |                170 |
	|    3 | Jack | 2007-04-06 |                100 |
	|    4 | Jill | 2007-04-06 |                220 |
	|    5 | Zara | 2007-06-06 |                300 |
	|    5 | Zara | 2007-02-06 |                350 |
	+------+------+------------+--------------------+
	7 rows in set (0.00 sec)

现在，假设你想要获取 daily_typing_pages 的最大值，那么你可以用如下命令来达到目的：

	SQL> SELECT MAX(daily_typing_pages)
	    -> FROM employee_tbl;
	+-------------------------+
	| MAX(daily_typing_pages) |
	+-------------------------+
	|                     350 |
	+-------------------------+
	1 row in set (0.00 sec)

你还可以使用 **GROUP BY** 子句，为每个名字（name）找出 daily_typing_pages 的最大值：

	SQL> SELECT id, name, MAX(daily_typing_pages)
	    -> FROM employee_tbl GROUP BY name;
	+------+------+-------------------------+
	| id   | name | MAX(daily_typing_pages) |
	+------+------+-------------------------+
	|    3 | Jack |                     170 |
	|    4 | Jill |                     220 |
	|    1 | John |                     250 |
	|    2 | Ram  |                     220 |
	|    5 | Zara |                     350 |
	+------+------+-------------------------+
	5 rows in set (0.00 sec)

你还可以将 **MIN** 函数同 **MAX** 函数一起使用，来找出最小值。试一下下面的例子：

	SQL> SELECT MIN(daily_typing_pages) least, MAX(daily_typing_pages) max
	    -> FROM employee_tbl;
	+-------+------+
	| least | max  |
	+-------+------+
	|   100 |  350 |
	+-------+------+
	1 row in set (0.01 sec)

你还可以将 **MIN** 函数同 **MAX** 函数一起使用，来找出最小值。试一下下面的例子：

	SQL> SELECT MIN(daily_typing_pages) least, 
	    -> MAX(daily_typing_pages) max
	    -> FROM employee_tbl;
	+-------+------+
	| least | max  |
	+-------+------+
	|   100 |  350 |
	+-------+------+
	1 row in set (0.01 sec)
