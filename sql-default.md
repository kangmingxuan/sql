# DEFAULT 约束 #

----------

DEFAULT 约束在 INSERT INTO 语句没有提供的情况下，为指定字段设置默认值。

## 示例： ##

例如，下述 SQL 语句创建了一个名为 CUSTOMERS 的新表，并添加了五个字段。这里，SALARY 字段的默认值为 5000。因此，如果 INSERT INTO 没有为该字段提供值的话，该字段就为默认值 5000。

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2) DEFAULT 5000.00,       
	       PRIMARY KEY (ID)
	);

如果 CUSTOMERS 表已经存在，此时再要给 SALARY 字段添加 DEFAULT 约束的话，你需要类似下面的语句：

	ALTER TABLE CUSTOMERS
	   MODIFY SALARY  DECIMAL (18, 2) DEFAULT 5000.00;

## 删除 DEFAULT 约束： ##

要删除 DEFAULT 约束的话，请使用下面的 SQL 语句：

	ALTER TABLE CUSTOMERS
	   ALTER COLUMN SALARY DROP DEFAULT;

