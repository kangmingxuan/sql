# INSERT 语句 #

SQL **INSERT INTO** 语句用于向数据库中的表添加新行。

## 语法： ##

INSERT INTO 有两种基本的语法，第一种语法格式如下：

    INSERT INTO TABLE_NAME (column1, column2, column3,...columnN) 
    VALUES (value1, value2, value3,...valueN);

这里 column1, column2,...columnN 是表中字段的名字，你必须为新记录的这些字段填充数据。

如果要为表中所有的字段都添加数据的话，就不需要指定字段名了。不过这种情况下，必须保证值的顺序按照表中字段出现的顺序排列。 此时 SQL INSERT INTO 语句的语法如下：

    INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);

## 示例： ##

下面的语句将在 CUSTOMERS 表中创建六条新记录：

    INSERT INTO CUSTOMERS (ID,NAME,AGE,ADDRESS,SALARY)
    VALUES (1, 'Ramesh', 32, 'Ahmedabad', 2000.00 );
    
    INSERT INTO CUSTOMERS (ID,NAME,AGE,ADDRESS,SALARY)
    VALUES (2, 'Khilan', 25, 'Delhi', 1500.00 );
    
    INSERT INTO CUSTOMERS (ID,NAME,AGE,ADDRESS,SALARY)
    VALUES (3, 'kaushik', 23, 'Kota', 2000.00 );
    
    INSERT INTO CUSTOMERS (ID,NAME,AGE,ADDRESS,SALARY)
    VALUES (4, 'Chaitali', 25, 'Mumbai', 6500.00 );
    
    INSERT INTO CUSTOMERS (ID,NAME,AGE,ADDRESS,SALARY)
    VALUES (5, 'Hardik', 27, 'Bhopal', 8500.00 );
    
    INSERT INTO CUSTOMERS (ID,NAME,AGE,ADDRESS,SALARY)
    VALUES (6, 'Komal', 22, 'MP', 4500.00 );

你也可以使用第二种语法在表中创建一条新记录：

    INSERT INTO CUSTOMERS 
    VALUES (7, 'Muffy', 24, 'Indore', 10000.00 );

上面所有的语句执行完毕之后，CUSTOMERS 表中所有的记录应当如下所示：

    +----+----------+-----+-----------+----------+
    | ID | NAME     | AGE | ADDRESS   | SALARY   |
    +----+----------+-----+-----------+----------+
    |  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
    |  2 | Khilan   |  25 | Delhi     |  1500.00 |
    |  3 | kaushik  |  23 | Kota      |  2000.00 |
    |  4 | Chaitali |  25 | Mumbai    |  6500.00 |
    |  5 | Hardik   |  27 | Bhopal    |  8500.00 |
    |  6 | Komal    |  22 | MP        |  4500.00 |
    |  7 | Muffy    |  24 | Indore    | 10000.00 |
    +----+----------+-----+-----------+----------+

## 利用 ##

你还可以用 SELECT 语句将一个表中相应字段的数据填充到另一个表中，其语法形式如下：

    INSERT INTO first_table_name [(column1, column2, ... columnN)] 
       SELECT column1, column2, ...columnN 
       FROM second_table_name
       [WHERE condition];
