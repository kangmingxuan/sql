# CHECK 约束 #

----------

CHECK 约束使用某一条件来对记录中的值进行检查。如果条件最终为假（false），即约束条件不能得到满足，则该记录不能写入数据表中。

## 示例： ##

例如，下述 SQL 语句创建了一个名为 CUSTOMERS 的新表，并为其添加了五个字段。在此，我们为 AGE 字段设置了 CHECK 约束，以拒绝任何年龄低于 18 的顾客：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL CHECK (AGE >= 18),
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2),       
	       PRIMARY KEY (ID)
	);

如果 CUSTOMERS 表已经存在，再要为 AGE 字段设置 CHECK 约束的话，就需要像下面这样写 SQL 语句：

	ALTER TABLE CUSTOMERS
	   MODIFY AGE INT NOT NULL CHECK (AGE >= 18 );

或者也可以使用下面的语法，该语法还支持对作用于多个字段的约束命名：

	ALTER TABLE CUSTOMERS
	   ADD CONSTRAINT myCheckConstraint CHECK(AGE >= 18);

## 删除 CHECK 约束： ##

要删除 CHECK 约束的话，请使用下面的 SQL 语句，不过该语句在 MySQL 中不起作用：

	ALTER TABLE CUSTOMERS
	   DROP CONSTRAINT myCheckConstraint;
