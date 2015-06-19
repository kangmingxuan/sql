# 外键 #

----------

外键用于将两个数据表连接在一起，有时候也被称作“参照键”。

外键为单一字段或者多个字段的组合，并与另外一个数据表的主键相匹配。

**两个表之间的关系是：一个表的主键与另一个表的外键相匹配。**

## 示例： ##

考虑如下两个表的结构：

CUSTOMERS 表：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2),       
	       PRIMARY KEY (ID)
	);

ORDERS 表：

	CREATE TABLE ORDERS (
	       ID          INT        NOT NULL,
	       DATE        DATETIME, 
	       CUSTOMER_ID INT references CUSTOMERS(ID),
	       AMOUNT     double,
	       PRIMARY KEY (ID)
	);

如果 ORDERS 表已经存在，并且没有设置外键，那么可以使用下面的语法来修改数据表以指定外键。

	ALTER TABLE ORDERS 
	   ADD FOREIGN KEY (Customer_ID) REFERENCES CUSTOMERS (ID);

## 删除外键约束： ##

要删除外键约束的话，语法如下所示：

	ALTER TABLE ORDERS
	   DROP FOREIGN KEY;
