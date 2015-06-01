# ALTER TABLE 命令 #

----------

SQL **ALTER TABLE** 命令用于添加、删除或者更改现有数据表中的列。

你还可以用 ALTER TABLE 命令来添加或者删除现有数据表上的约束。

## 语法： ##

使用 ALTER TABLE 在现有的数据表中**添加新列**的基本语法如下：

	ALTER TABLE table_name ADD column_name datatype;

使用 ALTER TABLE 在现有的数据表中**删除列**的基本语法如下：

	ALTER TABLE table_name DROP COLUMN column_name;


使用 ALTER TABLE 更改现有的数据表中**列的数据类型**的基本语法如下：

	ALTER TABLE table_name MODIFY COLUMN column_name datatype;


使用 ALTER TABLE 给某列添加 **NOT NULL 约束** 的基本语法如下：

	ALTER TABLE table_name MODIFY column_name datatype NOT NULL;

使用 ALTER TABLE 给数据表添加 **唯一约束** 的基本语法如下：

	ALTER TABLE table_name 
	ADD CONSTRAINT MyUniqueConstraint UNIQUE(column1, column2...);

使用 ALTER TABLE 给数据表添加 **CHECK 约束** 的基本语法如下：

	ALTER TABLE table_name 
	ADD CONSTRAINT MyUniqueConstraint CHECK (CONDITION);

使用 ALTER TABLE 给数据表添加 **主键约束** 的基本语法如下：

	ALTER TABLE table_name 
	ADD CONSTRAINT MyPrimaryKey PRIMARY KEY (column1, column2...);

使用 ALTER TABLE 从数据表中 **删除约束** 的基本语法如下：

	ALTER TABLE table_name 
	DROP CONSTRAINT MyUniqueConstraint;

如果你在使用 MySQL，代码应当如下：

	ALTER TABLE table_name 
	DROP INDEX MyUniqueConstraint;

使用 ALTER TABLE 从数据表中 **删除主键约束** 的基本语法如下：

	ALTER TABLE table_name 
	DROP CONSTRAINT MyPrimaryKey;

如果你在使用 MySQL，代码应当如下：

	ALTER TABLE table_name 
	DROP PRIMARY KEY;

## 示例： ##

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

下面的示例展示了如何在现有的表中添加新的一列：

	ALTER TABLE CUSTOMERS ADD SEX char(1);

现在，CUSTOMERS 已经被更改了，SELECT 语句的输出应当如下所示：

	+----+---------+-----+-----------+----------+------+
	| ID | NAME    | AGE | ADDRESS   | SALARY   | SEX  |
	+----+---------+-----+-----------+----------+------+
	|  1 | Ramesh  |  32 | Ahmedabad |  2000.00 | NULL |
	|  2 | Ramesh  |  25 | Delhi     |  1500.00 | NULL |
	|  3 | kaushik |  23 | Kota      |  2000.00 | NULL |
	|  4 | kaushik |  25 | Mumbai    |  6500.00 | NULL |
	|  5 | Hardik  |  27 | Bhopal    |  8500.00 | NULL |
	|  6 | Komal   |  22 | MP        |  4500.00 | NULL |
	|  7 | Muffy   |  24 | Indore    | 10000.00 | NULL |
	+----+---------+-----+-----------+----------+------+

下面的示例展示了如何从 CUSTOMERS 表中删除 SEX 列：

	ALTER TABLE CUSTOMERS DROP SEX;

现在，CUSTOMERS 已经被更改了，SELECT 语句的输出应当如下所示：

	+----+---------+-----+-----------+----------+
	| ID | NAME    | AGE | ADDRESS   | SALARY   |
	+----+---------+-----+-----------+----------+
	|  1 | Ramesh  |  32 | Ahmedabad |  2000.00 |
	|  2 | Ramesh  |  25 | Delhi     |  1500.00 |
	|  3 | kaushik |  23 | Kota      |  2000.00 |
	|  4 | kaushik |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik  |  27 | Bhopal    |  8500.00 |
	|  6 | Komal   |  22 | MP        |  4500.00 |
	|  7 | Muffy   |  24 | Indore    | 10000.00 |
	+----+---------+-----+-----------+----------+
