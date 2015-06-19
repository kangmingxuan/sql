# 第一范式（1NF） #

----------

第一范式设定了对数据库进行组织的最基本的规范：

- 定义需要的数据项，因为这些项将会成为数据表中的字段。将相关的数据项放在一个表中。
- 保证不存在重复的数据。
- 保证有一个主键。

## 1NF 的第一规则： ##

你必须定义所需的数据项。这意味着查看要存储的数据，按照字段对其进行组织，定义各个字段的数据类型，最终将相关的字段放在同一个表中。

例如，将所有与会议地点相关的字段放在 Location 表中，将所有同与会成员相关的字段放在 MemberDetails 表中等等。

## 1NF 的第二规则： ##

下一步是保证不存在重复的数据集合。考虑如下的数据表：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25),
	       ORDERS   VARCHAR(155)
	);

如果我们用同一个顾客的多笔订单来填充该表，将会得到类似下面的数据表：

<table>
   <tr>
      <td>ID</td>
      <td>NAME</td>
      <td>AGE</td>
      <td>ADDRESS</td>
      <td>ORDERS</td>
   </tr>
   <tr>
      <td>100</td>
      <td>Sachin</td>
      <td>36</td>
      <td>Lower West Side</td>
      <td>Cannon XL-200</td>
   </tr>
   <tr>
      <td>100</td>
      <td>Sachin</td>
      <td>36</td>
      <td>Lower West Side</td>
      <td>Battery XL-200</td>
   </tr>
   <tr>
      <td>100</td>
      <td>Sachin</td>
      <td>36</td>
      <td>Lower West Side</td>
      <td>Tripod Large</td>
   </tr>
</table>

但是，按照 1NF 我们必须保证没有重复的数据集合。所以，可以将上表分成两部分，然后使用一个键将两个表连接起来。

CUSTOMERS 表：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25),
	       PRIMARY KEY (ID)
	);

表中记录如下：

<table>
   <tr>
      <td>ID</td>
      <td>NAME</td>
      <td>AGE</td>
      <td>ADDRESS</td>
   </tr>
   <tr>
      <td>100</td>
      <td>Sachin</td>
      <td>36</td>
      <td>Lower West Side</td>
   </tr>
</table>

ORDERS 表：

	CREATE TABLE ORDERS(
	       ID   INT              NOT NULL,
	       CUSTOMER_ID INT       NOT NULL,
	       ORDERS   VARCHAR(155),
	       PRIMARY KEY (ID)
	);

表中记录如下：

<table>
   <tr>
      <td>ID</td>
      <td>CUSTOMER_ID</td>
      <td>ORDERS</td>
   </tr>
   <tr>
      <td>10</td>
      <td>100</td>
      <td>Cannon XL-200</td>
   </tr>
   <tr>
      <td>11</td>
      <td>100</td>
      <td>Battery XL-200</td>
   </tr>
   <tr>
      <td>12</td>
      <td>100</td>
      <td>Tripod Large</td>
   </tr>
</table>

## 1NF 的第三规则： ##

第一范式的最后一条规则是，为每一个数据表创建一个主键。