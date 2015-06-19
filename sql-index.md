# 索引约束 #

----------

索引用于在数据库中快速地创建和检索数据。索引可以由表中的一个或者多个字段创建。创建索引时，每一行都会获得一个 ROWID（在数据进行排序之前）。

合理运用索引可以提高大型数据库的性能。但是，创建索引之前还是要三思而后行。为哪些字段创建索引，则取决于 SQL 查询最常用到到哪些字段。

## 示例： ##

例如，下面的 SQL 语句创建了一个名为 CUSTOMERS 的新表，并为其添加了五个字段：

	CREATE TABLE CUSTOMERS(
	       ID   INT              NOT NULL,
	       NAME VARCHAR (20)     NOT NULL,
	       AGE  INT              NOT NULL,
	       ADDRESS  CHAR (25) ,
	       SALARY   DECIMAL (18, 2),       
	       PRIMARY KEY (ID)
	);

现在，你就可以使用下面的语法来为一个或者多个字段创建索引了：

	CREATE INDEX index_name
	    ON table_name ( column1, column2.....);

例如，可以在 AGE 字段上创建索引，以优化对特定年龄的顾客的查询，其语法如下所示：

	CREATE INDEX idx_age
	    ON CUSTOMERS ( AGE );

## 删除索引约束： ##

要删除索引约束的话，可以使用下面的 SQL 语句：

	ALTER TABLE CUSTOMERS
	   DROP INDEX idx_age;

