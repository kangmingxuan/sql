# 逻辑运算符 #

考虑 CUSTOMERS 表，表中的记录如下所示：

	SQL> SELECT * FROM CUSTOMERS;
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
	7 rows in set (0.00 sec)

下面是一些关于如何使用 SQL 逻辑运算符的简单示例：

	SQL> SELECT * FROM CUSTOMERS WHERE AGE >= 25 AND SALARY >= 6500;
	+----+----------+-----+---------+---------+
	| ID | NAME     | AGE | ADDRESS | SALARY  |
	+----+----------+-----+---------+---------+
	|  4 | Chaitali |  25 | Mumbai  | 6500.00 |
	|  5 | Hardik   |  27 | Bhopal  | 8500.00 |
	+----+----------+-----+---------+---------+
	2 rows in set (0.00 sec)
	
	
	SQL> SELECT * FROM CUSTOMERS WHERE AGE >= 25 OR SALARY >= 6500;
	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  2 | Khilan   |  25 | Delhi     |  1500.00 |
	|  4 | Chaitali |  25 | Mumbai    |  6500.00 |
	|  5 | Hardik   |  27 | Bhopal    |  8500.00 |
	|  7 | Muffy    |  24 | Indore    | 10000.00 |
	+----+----------+-----+-----------+----------+
	5 rows in set (0.00 sec)
	
	SQL>  SELECT * FROM CUSTOMERS WHERE AGE IS NOT NULL;
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
	7 rows in set (0.00 sec)
	
	SQL> SELECT * FROM CUSTOMERS WHERE NAME LIKE 'Ko%';
	+----+-------+-----+---------+---------+
	| ID | NAME  | AGE | ADDRESS | SALARY  |
	+----+-------+-----+---------+---------+
	|  6 | Komal |  22 | MP      | 4500.00 |
	+----+-------+-----+---------+---------+
	1 row in set (0.00 sec)
	
	SQL> SELECT * FROM CUSTOMERS WHERE AGE IN ( 25, 27 );
	+----+----------+-----+---------+---------+
	| ID | NAME     | AGE | ADDRESS | SALARY  |
	+----+----------+-----+---------+---------+
	|  2 | Khilan   |  25 | Delhi   | 1500.00 |
	|  4 | Chaitali |  25 | Mumbai  | 6500.00 |
	|  5 | Hardik   |  27 | Bhopal  | 8500.00 |
	+----+----------+-----+---------+---------+
	3 rows in set (0.00 sec)
	
	SQL> SELECT * FROM CUSTOMERS WHERE AGE BETWEEN 25 AND 27;
	+----+----------+-----+---------+---------+
	| ID | NAME     | AGE | ADDRESS | SALARY  |
	+----+----------+-----+---------+---------+
	|  2 | Khilan   |  25 | Delhi   | 1500.00 |
	|  4 | Chaitali |  25 | Mumbai  | 6500.00 |
	|  5 | Hardik   |  27 | Bhopal  | 8500.00 |
	+----+----------+-----+---------+---------+
	3 rows in set (0.00 sec)
	
	SQL> SELECT AGE FROM CUSTOMERS 
	WHERE EXISTS (SELECT AGE FROM CUSTOMERS WHERE SALARY > 6500);
	+-----+
	| AGE |
	+-----+
	|  32 |
	|  25 |
	|  23 |
	|  25 |
	|  27 |
	|  22 |
	|  24 |
	+-----+
	7 rows in set (0.02 sec)
	
	SQL> SELECT * FROM CUSTOMERS 
	WHERE AGE > ALL (SELECT AGE FROM CUSTOMERS WHERE SALARY > 6500);
	+----+--------+-----+-----------+---------+
	| ID | NAME   | AGE | ADDRESS   | SALARY  |
	+----+--------+-----+-----------+---------+
	|  1 | Ramesh |  32 | Ahmedabad | 2000.00 |
	+----+--------+-----+-----------+---------+
	1 row in set (0.02 sec)
	
	SQL> SELECT * FROM CUSTOMERS 
	WHERE AGE > ANY (SELECT AGE FROM CUSTOMERS WHERE SALARY > 6500);
	+----+----------+-----+-----------+---------+
	| ID | NAME     | AGE | ADDRESS   | SALARY  |
	+----+----------+-----+-----------+---------+
	|  1 | Ramesh   |  32 | Ahmedabad | 2000.00 |
	|  2 | Khilan   |  25 | Delhi     | 1500.00 |
	|  4 | Chaitali |  25 | Mumbai    | 6500.00 |
	|  5 | Hardik   |  27 | Bhopal    | 8500.00 |
	+----+----------+-----+-----------+---------+
	4 rows in set (0.00 sec)
