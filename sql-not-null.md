# NOT NULL 约束 #

----------

默认情况下，数据表中的字段接受 NULL 值。如果你不想让某个字段接受 NULL 值，那么请为该字段定义此约束，以指明该字段不接受 NULL 值。

NULL 并不是指**没有**数据，而是指该字段数据**未知**。

## 示例： ##

例如，下述 SQL 语句创建了一个新的数据表 CUSTOMERS，并添加了五个字段，其中三个字段——ID、NAME和AGE——被指定为 NOT NULL：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2),       
	       PRIMARY KEY (ID)
	);

对于 Oracle 和 MySQL 来说，如果 CUSTOMERS 表已经存在，此时再要给 SALARY 字段添加 NOT NULL 约束的话，SQL 语句应当如下：

	ALTER TABLE CUSTOMERS
	   MODIFY SALARY  DECIMAL (18, 2) NOT NULL;
