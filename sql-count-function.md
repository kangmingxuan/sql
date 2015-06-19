# COUNT 函数 #

**COUNT**函数是 SQL 中最简单的函数了，对于统计由 SELECT 语句返回的记录非常有用。

要理解 COUNT 函数，请考虑  employee_tbl 表，表中的记录如下所示：

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

现在，假设你想要统计上表中记录的总数，那么可以依如下所示步骤达到目的：

	SQL>SELECT COUNT(*) FROM employee_tbl ;
	+----------+
	| COUNT(*) |
	+----------+
	|        7 |
	+----------+
	1 row in set (0.01 sec)

类似地，如果你想要统计 Zara 的数目，就可以像下面这样：

	SQL>SELECT COUNT(*) FROM employee_tbl
	    -> WHERE name="Zara";
	+----------+
	| COUNT(*) |
	+----------+
	|        2 |
	+----------+
	1 row in set (0.04 sec)

**注意：**所有的 SQL 查询都是不区分大小写的，因此在 WHERE 子句的条件中，ZARA 和 Zara 是没有任何区别的。
