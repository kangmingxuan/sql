# 子查询 #

----------

子查询（Sub Query）或者说内查询（Inner Query），也可以称作嵌套查询（Nested Query），是一种嵌套在其他 SQL 查询的 WHERE 子句中的查询。

子查询用于为主查询返回其所需数据，或者对检索数据进行进一步的限制。

子查询可以在 SELECT、INSERT、UPDATE 和 DELETE 语句中，同 =、<、>、>=、<=、IN、BETWEEN 等运算符一起使用。

使用子查询必须遵循以下几个规则：

- 子查询必须括在圆括号中。
- 子查询的 SELECT 子句中只能有一个列，除非主查询中有多个列，用于与子查询选中的列相比较。
- 子查询不能使用 ORDER BY，不过主查询可以。在子查询中，GROUP BY 可以起到同 ORDER BY 相同的作用。
- 返回多行数据的子查询只能同多值操作符一起使用，比如 IN 操作符。
- SELECT 列表中不能包含任何对 BLOB、ARRAY、CLOB 或者 NCLOB 类型值的引用。
- 子查询不能直接用在集合函数中。
- BETWEEN 操作符不能同子查询一起使用，但是 BETWEEN 操作符可以用在子查询中。

## SELECT 语句中的子查询 ##

通常情况下子查询都与 SELECT 语句一起使用，其基本语法如下所示：

	SELECT column_name [, column_name ]
	FROM   table1 [, table2 ]
	WHERE  column_name OPERATOR
	      (SELECT column_name [, column_name ]
	      FROM table1 [, table2 ]
	      [WHERE])

## 示例： ##

考虑 CUSTOMERS 表，表中记录如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  35 | Ahmedabad |  2000.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	|  6 | Komal    |  22 | MP        |  4500.00 |
	|  7 | Muffy    |  24 | Indore    | 10000.00 |
	+----+----------+-----+-----------+----------+

现在，让我们试一下在 SELECT 语句中进行子查询：

	SQL> SELECT * 
	     FROM CUSTOMERS 
	     WHERE ID IN (SELECT ID 
	                  FROM CUSTOMERS 
	                  WHERE SALARY > 4500) ;

上述语句的执行结果如下所示：

	+----+----------+-----+---------+----------+
	| ID | NAME     | AGE | ADDRESS | SALARY   |
	+----+----------+-----+---------+----------+
	|  4 | Chaitali |  25 | Mumbai  |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal  |  8500.00 |
	|  7 | Muffy    |  24 | Indore  | 10000.00 |
	+----+----------+-----+---------+----------+

## INSERT 语句中的子查询： ##

子查询还可以用在 INSERT 语句中。INSERT 语句可以将子查询返回的数据插入到其他表中。子查询中选取的数据可以被任何字符、日期或者数值函数所修饰。

其基本语法如下所示：

	INSERT INTO table_name [ (column1 [, column2 ]) ]
	           SELECT [ *|column1 [, column2 ]
	           FROM table1 [, table2 ]
	           [ WHERE VALUE OPERATOR ]

## 示例： ##

考虑与 CUSTOMERS 表拥有相似结构的  CUSTOMERS_BKP 表。现在要将 CUSTOMER 表中所有的数据复制到  CUSTOMERS_BKP 表中，代码如下：

	SQL> INSERT INTO CUSTOMERS_BKP
	     SELECT * FROM CUSTOMERS 
	     WHERE ID IN (SELECT ID 
	                  FROM CUSTOMERS) ;

## UPDATE 语句中的子查询： ##

子查询可以用在 UPDATE 语句中。当子查询同 UPDATE 一起使用的时候，既可以更新单个列，也可更新多个列。

其基本语法如下：

	UPDATE table
	SET column_name = new_value
	[ WHERE OPERATOR [ VALUE ]
	   (SELECT COLUMN_NAME
	   FROM TABLE_NAME)
	   [ WHERE) ]

## 示例： ##

假设我们有一份 CUSTOMERS_BKP 表作为 CUSTOMERS 表的备份。

下面的示例将 CUSTOMERS 表中所有 AGE 大于或者等于 27 的客户的 SALARY 字段都变为了原来的 0.25 倍：

	SQL> UPDATE CUSTOMERS
	     SET SALARY = SALARY * 0.25
	     WHERE AGE IN (SELECT AGE FROM CUSTOMERS_BKP
	                   WHERE AGE >= 27 );

这将影响两行数据，随后 CUSTOMERS 表中的记录将如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  35 | Ahmedabad |   125.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  2125.00 |
	|  6 | Komal    |  22 | MP        |  4500.00 |
	|  7 | Muffy    |  24 | Indore    | 10000.00 |
	+----+----------+-----+-----------+----------+

## DELETE 语句中的子查询： ##

如同前面提到的其他语句一样，子查询还可以同 DELETE 语句一起使用。

其基本语法如下所示：

	DELETE FROM TABLE_NAME
	[ WHERE OPERATOR [ VALUE ]
	   (SELECT COLUMN_NAME
	   FROM TABLE_NAME)
	   [ WHERE) ]

## 示例： ##

假设我们有一份 CUSTOMERS_BKP 表作为 CUSTOMERS 表的备份。

下面的示例将从 CUSTOMERS 表中删除所有 AGE 大于或者等于 27 的记录：

	SQL> DELETE FROM CUSTOMERS
	     WHERE AGE IN (SELECT AGE FROM CUSTOMERS_BKP
	                   WHERE AGE > 27 );

这将影响两行数据，随后 CUSTOMERS 表中的记录将如下所示：

	+----+----------+-----+---------+----------+
	| ID | NAME     | AGE | ADDRESS | SALARY   |
	+----+----------+-----+---------+----------+
	|  2 | Khilan   |  25 | Delhi   |  1500.00 |
	|  3 | kaushik  |  23 | Kota    |  2000.00 |
	|  4 | Chaitali |  25 | Mumbai  |  6500.00 |
	|  6 | Komal    |  22 | MP      |  4500.00 |
	|  7 | Muffy    |  24 | Indore  | 10000.00 |
	+----+----------+-----+---------+----------+

