# NULL 值 #

----------

SQL 中，**NULL** 用于表示缺失的值。数据表中的 NULL 值表示该值所处的字段为空。

值为 NULL 的字段没有值。尤其要明白的是，NULL 值与 0 或者包含空白（spaces）的字段是不同的。

## 语法： ##

创建表的时候，NULL的基本语法如下：

	SQL> CREATE TABLE CUSTOMERS(
	   ID   INT              NOT NULL,
	   NAME VARCHAR (20)     NOT NULL,
	   AGE  INT              NOT NULL,
	   ADDRESS  CHAR (25) ,
	   SALARY   DECIMAL (18, 2),       
	   PRIMARY KEY (ID)
	);

这里，**NOT NULL**表示对于给定列，必须按照其数据类型明确赋值。有两列并没有使用 NOT NULL 来限定，也就是说这些列可以为 NULL。

值为 NULL 的字段是在记录创建的过程中留空的字段。

## 示例： ##

NULL 值会给选取数据带来麻烦。不过，因为 NULL 和其他任何值作比较，其结果总是未知的，所以含有 NULL 的记录不会包含在最终结果里面。

必须使用 **IS NULL** 或者 **IS NOT NULL** 来检测某个字段是否为 NULL。

考虑下面的 CUSTOMERS 数据表，里面包含的记录如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	|  6 | Komal    |  22 | MP        |          |
	|  7 | Muffy    |  24 | Indore    |          |
	+----+----------+-----+-----------+----------+

下面是 **IS NOT NULL** 运算符的用法：

	SQL> SELECT  ID, NAME, AGE, ADDRESS, SALARY
	     FROM CUSTOMERS
	     WHERE SALARY IS NOT NULL;

上面语句的运行结果如下：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	+----+----------+-----+-----------+----------+

下面是 **IS NULL** 运算符的用法：

	SQL> SELECT  ID, NAME, AGE, ADDRESS, SALARY
	     FROM CUSTOMERS
	     WHERE SALARY IS NULL;

其运行结果如下：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  6 | Komal    |  22 | MP        |          |
	|  7 | Muffy    |  24 | Indore    |          |
	+----+----------+-----+-----------+----------+
