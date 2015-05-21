# LIKE 子句 #

----------

SQL **LIKE** 子句通过通配符来将一个值同其他相似的值作比较。可以同 LIKE 运算符一起使用的通配符有两个：

- 百分号（%）
- 下划线（_）

百分号代表零个、一个或者多个字符。下划线则代表单个数字或者字符。两个符号可以一起使用。

## 语法： ##

% 和 _ 的基本语法如下：

	SELECT FROM table_name
	WHERE column LIKE 'XXXX%'
	
	or 
	
	SELECT FROM table_name
	WHERE column LIKE '%XXXX%'
	
	or
	
	SELECT FROM table_name
	WHERE column LIKE 'XXXX_'
	
	or
	
	SELECT FROM table_name
	WHERE column LIKE '_XXXX'
	
	or
	
	SELECT FROM table_name
	WHERE column LIKE '_XXXX_'

你可以将多个条件用 AND 或者 OR　连接在一起。这里，XXXX　为任何数字值或者字符串。

## 示例： ##

下面这些示例中，每个 WHERE 子句都有不同的 LIKE 子句，展示了 % 和 _ 的用法:

<table>
   <tr>
      <td>语句</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '200%'</td>
      <td>找出所有 200 打头的值</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '%200%'</td>
      <td>找出所有含有 200 的值</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '_00%'</td>
      <td>找出所有第二位和第三位为 0 的值</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '2_%_%'</td>
      <td>找出所有以 2 开始，并且长度至少为 3 的值</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '%2'</td>
      <td>找出所有以 2 结尾的值</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '_2%3'</td>
      <td>找出所有第二位为 2，并且以3结束的值</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '2___3'</td>
      <td>找出所有以 2 开头以 3 结束的五位数</td>
   </tr>
</table>

让我们来看一个真实的例子，考虑含有如下所示记录的 CUSTOMERS 表：

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

下面的例子将 CUSTOMERS 表中 SALARY 字段以 200 开始的记录显示出来：

	SQL> SELECT * FROM CUSTOMERS
	WHERE SALARY LIKE '200%';

结果如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	+----+----------+-----+-----------+----------+
