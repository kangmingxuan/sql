# 临时表 #

----------

某些关系型数据库管理系统支持临时表。临时表是一项很棒的特性，能够让你像操作普通的 SQL 数据表一样，使用 SELECT、UPDATE 和 JOIN 等功能来存储或者操作中间结果。

临时表有时候对于保存临时数据非常有用。有关临时表你需要知道的最重要的一点是，它们会在当前的终端会话结束后被删除。

临时表自 MySQL 3.23 起受到支持。如果你的 MySQL 版本比 3.23 还老，那么你就不能使用临时表了，不过你可以使用堆表（heap table）。

如先前所言，临时表只在会话期间存在。如果你在 PHP 脚本中操作数据库，那么临时表将在脚本执行完毕时被自动销毁。如果你是通过 MySQL 的客户端程序连接到 MySQL 数据库服务器的，那么临时表将会存在到你关闭客户端或者手动将其删除。

## 示例： ##

下面的示例向你展示了如何使用临时表：

	mysql> CREATE TEMPORARY TABLE SALESSUMMARY (
	    -> product_name VARCHAR(50) NOT NULL
	    -> , total_sales DECIMAL(12,2) NOT NULL DEFAULT 0.00
	    -> , avg_unit_price DECIMAL(7,2) NOT NULL DEFAULT 0.00
	    -> , total_units_sold INT UNSIGNED NOT NULL DEFAULT 0
	);
	Query OK, 0 rows affected (0.00 sec)
	
	mysql> INSERT INTO SALESSUMMARY
	    -> (product_name, total_sales, avg_unit_price, total_units_sold)
	    -> VALUES
	    -> ('cucumber', 100.25, 90, 2);
	
	mysql> SELECT * FROM SALESSUMMARY;
	+--------------+-------------+----------------+------------------+
	| product_name | total_sales | avg_unit_price | total_units_sold |
	+--------------+-------------+----------------+------------------+
	| cucumber     |      100.25 |          90.00 |                2 |
	+--------------+-------------+----------------+------------------+
	1 row in set (0.00 sec)

当你下达 **SHOW TABLES** 命令的时候，临时表是不会出现在结果列表当中的。现在，如果你退出 MySQL 会话，然后再执行 SELECT 命令的话，你将不能从数据库中取回任何数据，你的临时表也已经不复存在了。

## 删除临时表： ##

默认情况下，所有的临时表都由 MySQL 在数据库连接关闭时删除。不过，有时候你还是会想要在会话期间将其删除，此时你需要使用 DROP TABLE 命令来达到目的。

下面是删除临时表的示例：

	mysql> CREATE TEMPORARY TABLE SALESSUMMARY (
	    -> product_name VARCHAR(50) NOT NULL
	    -> , total_sales DECIMAL(12,2) NOT NULL DEFAULT 0.00
	    -> , avg_unit_price DECIMAL(7,2) NOT NULL DEFAULT 0.00
	    -> , total_units_sold INT UNSIGNED NOT NULL DEFAULT 0
	);
	Query OK, 0 rows affected (0.00 sec)
	
	mysql> INSERT INTO SALESSUMMARY
	    -> (product_name, total_sales, avg_unit_price, total_units_sold)
	    -> VALUES
	    -> ('cucumber', 100.25, 90, 2);
	
	mysql> SELECT * FROM SALESSUMMARY;
	+--------------+-------------+----------------+------------------+
	| product_name | total_sales | avg_unit_price | total_units_sold |
	+--------------+-------------+----------------+------------------+
	| cucumber     |      100.25 |          90.00 |                2 |
	+--------------+-------------+----------------+------------------+
	1 row in set (0.00 sec)
	mysql> DROP TABLE SALESSUMMARY;
	mysql>  SELECT * FROM SALESSUMMARY;
	ERROR 1146: Table 'TUTORIALS.SALESSUMMARY' doesn't exist
