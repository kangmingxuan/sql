# SUM 函数 #

**SUM**函数用于找出表中记录在某字段处的总和。

要理解 **SUM** 函数，请考虑 **employee_tbl** 表，表中记录如下所示：

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

现在，假设你想要获取 daily_typing_pages 的总和，那么你可以用如下命令来达到目的：

	SQL> SELECT SUM(daily_typing_pages)
	    -> FROM employee_tbl;
	+-------------------------+
	| SUM(daily_typing_pages) |
	+-------------------------+
	|                    1610 |
	+-------------------------+
	1 row in set (0.00 sec)

你还可以使用 **GROUP BY** 子句来得出不同记录分组的总和。下面的例子将会计算得出每个人的总和，，你将能够得到每个人每天打的总页数。

	SQL> SELECT name, SUM(daily_typing_pages)
	    -> FROM employee_tbl GROUP BY name;

