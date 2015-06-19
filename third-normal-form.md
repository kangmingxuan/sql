# 第三范式（3NF） #

----------

一个数据表符合第三范式，当其满足：

- 符合第二范式；
- 所有的非主键字段都依赖于主键；

非主键字段之间的依赖关系存在于数据之中。例如下表中，街道（street）、城市（city）和省份（state）显然与邮政编码（zip Code）之间存在密不可分的关系。

	CREATE TABLE CUSTOMERS(
	       CUST_ID       INT              NOT NULL,
	       CUST_NAME     VARCHAR (20)      NOT NULL,
	       DOB           DATE,
	       STREET        VARCHAR(200),
	       CITY          VARCHAR(100),
	       STATE         VARCHAR(100),
	       ZIP           VARCHAR(12),
	       EMAIL_ID      VARCHAR(256),
	       PRIMARY KEY (CUST_ID)
	);

邮政编码和地址之间的关系称作传递相关性（transitive dependency）。要使得数据表符合第三范式，需要将街道、城市、省份等字段移到另一张表中，可以称其为 Zip Code 表：

	CREATE TABLE ADDRESS(
	       ZIP           VARCHAR(12),
	       STREET        VARCHAR(200),
	       CITY          VARCHAR(100),
	       STATE         VARCHAR(100),
	       PRIMARY KEY (ZIP)
	);

接着，按照如下方式更改 CUSTOMERS 表：

	CREATE TABLE CUSTOMERS(
	       CUST_ID       INT              NOT NULL,
	       CUST_NAME     VARCHAR (20)      NOT NULL,
	       DOB           DATE,
	       ZIP           VARCHAR(12),
	       EMAIL_ID      VARCHAR(256),
	       PRIMARY KEY (CUST_ID)
	);

移除传递相关性可以起到事半功倍的效果。首先是数据冗余度降低了，数据库体积因此缩小。第二个好处是保证数据完整性。当重复数据改变的时候，很有可能只更新部分数据，尤其是当其分布在数据库的各个地方的情况下。例如，如果地址和邮政编码分别存储在三个或者四个不同的数据表中，那么任何对邮编的改变，都需要对这三个或者四个表同时进行更改。
