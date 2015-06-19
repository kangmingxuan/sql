# 第二范式（2NF） #

----------

第二范式规定，数据表必须符合第一范式，并且所有字段与主键之间不存在部分依赖关系。

考虑顾客与订单之间的关系，你可能会想要存储顾客 ID、顾客姓名、订单 ID、订单明细以及购买日期：

	CREATE TABLE CUSTOMERS(
	       CUST_ID    INT              NOT NULL,
	       CUST_NAME VARCHAR (20)      NOT NULL,
	       ORDER_ID   INT              NOT NULL,
	       ORDER_DETAIL VARCHAR (20)  NOT NULL,
	       SALE_DATE  DATETIME,
	       PRIMARY KEY (CUST_ID, ORDER_ID)
	);

该表符合第一范式，因为它满足第一范式的所有规则。表中的主键有 CUST_ID 和 ORDER_ID。二者一起作为主键，我们假定同一个顾客不会购买相同的东西。

然而，该表不符合第二范式，因为表中的字段和主键之间存在部分依赖关系。CUST_NAME 依赖于 CUST_ID，而 CUST_NAME 和所购物品之间没有直接的联系。订单明细和购买日期依赖于 ORDER_ID，但是他们并不依赖于 CUST_ID，因为 CUST_ID 和 ORDER_DETAIL 以及 SALE_DATE 之间并不存在联系。

要使该表遵守第二范式，你需要将其分为三个数据表。

首先，创建如下的数据表来保存客户详情：

	CREATE TABLE CUSTOMERS(
	       CUST_ID    INT              NOT NULL,
	       CUST_NAME VARCHAR (20)      NOT NULL,
	       PRIMARY KEY (CUST_ID)
	);

接着创建一个表来存储每个订单的详细信息：

	CREATE TABLE ORDERS(
	       ORDER_ID   INT              NOT NULL,
	       ORDER_DETAIL VARCHAR (20)  NOT NULL,
	       PRIMARY KEY (ORDER_ID)
	);

最后，创建一个表来存储 CUST_ID 和 ORDER_ID 来记录同一顾客的所有订单：

	CREATE TABLE CUSTMERORDERS(
	       CUST_ID    INT              NOT NULL,
	       ORDER_ID   INT              NOT NULL,
	       SALE_DATE  DATETIME,
	       PRIMARY KEY (CUST_ID, ORDER_ID)
	);
