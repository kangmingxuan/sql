# 使用序列 #

----------

序列是根据需要产生的一组有序整数：1, 2, 3 ... 序列在数据库中经常用到，因为许多应用要求数据表中的的每一行都有一个唯一的值，序列为此提供了一种简单的方法。

本节阐述在 MySQL 中如何使用序列。

## 使用 AUTO_INCREMENT 列： ##

在 MySQL 中使用序列最简单的方式是，把某列定义为 AUTO_INCREMENT，然后将剩下的事情交由 MySQL 处理：

## 示例： ##

试一下下面的例子，该例将会创建一张新表，然后再里面插入几条记录，添加记录时并不需要指定记录的 ID，因为该列的值由 MySQL 自动增加。

	mysql> CREATE TABLE INSECT
	    -> (
	    -> id INT UNSIGNED NOT NULL AUTO_INCREMENT,
	    -> PRIMARY KEY (id),
	    -> name VARCHAR(30) NOT NULL, # type of insect
	    -> date DATE NOT NULL, # date collected
	    -> origin VARCHAR(30) NOT NULL # where collected
	);
	Query OK, 0 rows affected (0.02 sec)
	mysql> INSERT INTO INSECT (id,name,date,origin) VALUES
	    -> (NULL,'housefly','2001-09-10','kitchen'),
	    -> (NULL,'millipede','2001-09-10','driveway'),
	    -> (NULL,'grasshopper','2001-09-10','front yard');
	Query OK, 3 rows affected (0.02 sec)
	Records: 3  Duplicates: 0  Warnings: 0
	mysql> SELECT * FROM INSECT ORDER BY id;
	+----+-------------+------------+------------+
	| id | name        | date       | origin     |
	+----+-------------+------------+------------+
	|  1 | housefly    | 2001-09-10 | kitchen    |
	|  2 | millipede   | 2001-09-10 | driveway   |
	|  3 | grasshopper | 2001-09-10 | front yard |
	+----+-------------+------------+------------+
	3 rows in set (0.00 sec)

## 获取 AUTO_INCREMENT 值： ##

LAST_INSERT_ID() 是一个 SQL 函数，可以用在任何能够执行 SQL 语句地方。另外，Perl 和 PHP 各自提供了其独有的函数，用于获得最后一条记录的 AUTO_INCREMENT 值。

## Perl 示例： ##

使用 mysql_insertid 属性来获取 SQL 查询产生的 AUTO_INCREMENT 值。根据执行查询的方式不同，该属性可以通过数据库句柄或者语句句柄来访问。下面的示例通过数据库句柄取得自增值：

	$dbh->do ("INSERT INTO INSECT (name,date,origin)
	VALUES('moth','2001-09-14','windowsill')");
	my $seq = $dbh->{mysql_insertid};

## PHP 示例： ##

在执行完会产生自增值的查询后，可以通过调用 mysql_insert_id() 来获取此值：

	mysql_query ("INSERT INTO INSECT (name,date,origin)
	VALUES('moth','2001-09-14','windowsill')", $conn_id);
	$seq = mysql_insert_id ($conn_id);

## 重新编号现有序列： ##

当你从表中删除了很多记录后，可能会想要对所有的记录重新定序。只要略施小计就能达到此目的，不过如果你的表与其他表之间存在连接的话，请千万小心。

当你觉得不得不对 AUTO_INCREMENT 列重新定序时，从表中删除该列，然后再将其添加回来，就可以达到目的了。下面的示例展示了如何使用这种方法，为 INSECT 表中的 ID 值重新定序：

	mysql> ALTER TABLE INSECT DROP id;
	mysql> ALTER TABLE insect
	    -> ADD id INT UNSIGNED NOT NULL AUTO_INCREMENT FIRST,
	    -> ADD PRIMARY KEY (id);

## 从特定值的序列 ##

默认情况下，MySQL 中序列的起始值为 1，不过你可以在创建数据表的时候，指定任意其他值。下面的示例中，MySQL 将序列的起始值设为 100：

	mysql> CREATE TABLE INSECT
	    -> (
	    -> id INT UNSIGNED NOT NULL AUTO_INCREMENT = 100,
	    -> PRIMARY KEY (id),
	    -> name VARCHAR(30) NOT NULL, # type of insect
	    -> date DATE NOT NULL, # date collected
	    -> origin VARCHAR(30) NOT NULL # where collected
	);

或者，你也可以先创建数据表，然后使用 ALTER TABLE 来设置序列的起始值：

	mysql> ALTER TABLE t AUTO_INCREMENT = 100;
