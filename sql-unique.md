# UNIQUE 约束 #

----------

UNIQUE 约束使得某一字段对任意两条记录来说都不能相同。例如，在 CUSTOMERS 表中，你或许想让任何人的年龄（age）都不相同。

## 示例： ##

例如，下述 SQL 语句创建了一个名为 CUSTOMERS 的新表，并添加了五个字段，其中 AGE 字段被设为 UNIQUE，于是任意两条记录的 AGE 都不同：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL UNIQUE,
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2),       
	       PRIMARY KEY (ID)
	);

如果 CUSTOMERS 表已经存在，再要为 AGE 字段添加 UNIQUE 约束的话，你需要像下面这样写 SQL 语句：

	ALTER TABLE CUSTOMERS
	   MODIFY AGE INT NOT NULL UNIQUE;

还可以使用如下所示的语法，该语法还支持对作用于多个字段的约束进行命名：

	ALTER TABLE CUSTOMERS
	   ADD CONSTRAINT myUniqueConstraint UNIQUE(AGE, SALARY);

## 删除 UNIQUE 约束 ##

要删除 UNIQUE 约束的话，请使用如下 SQL 语句：

	ALTER TABLE CUSTOMERS
	   DROP CONSTRAINT myUniqueConstraint;

如果你在使用 MySQL，那么下面的语法也是可行的：

	ALTER TABLE CUSTOMERS
	   DROP INDEX myUniqueConstraint;

