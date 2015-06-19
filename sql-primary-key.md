# 主键约束 #

----------

主键是数据表中唯一确定一条记录的字段。主键必须包含唯一值，并且不能为 NULL。

每张数据表只能有一个主键，不过一个主键可以包含一个或者多个字段。如果主键由多个字段组合而成，这些字段就被称作**组合键**。

如果一个字段被定义为了某表的主键，则任意两条记录在该字段处不能相同。

**注意：**在创建数据表的时候，需要用到这些概念。

## 创建主键： ##

如下是将 ID 定义为 CUSTOMERS 表主键的语法：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2),       
	       PRIMARY KEY (ID)
	);

如果 CUSTOMERS 表已经存在了，再要将 ID 定义为 主键的话，请使用下面的语句：

	ALTER TABLE CUSTOMER ADD PRIMARY KEY (ID);

**注意：**如果你要使用 ALTER TABLE 语句来添加主键，那么主键所在的列必须已经被声明为 NOT NULL 了。

要用多个字段来定义主键的话，请使用如下 SQL 语法：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2),        
	       PRIMARY KEY (ID, NAME)
	);

如果 CUSTOMERS 表已经存在，此时再要将 ID 和 NAMES 字段定义为主键的话，请使用如下 SQL 语法：

	ALTER TABLE CUSTOMERS 
	   ADD CONSTRAINT PK_CUSTID PRIMARY KEY (ID, NAME);

## 删除主键： ##

你可以将主键约束从数据表中删除，语法如下：

	ALTER TABLE CUSTOMERS DROP PRIMARY KEY ;
