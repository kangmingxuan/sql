# 通配符 #

----------

我们已经讨论过 SQL 的 **LIKE** 操作符了，它可以利用通配符来对两个相似的值作比较。

SQL 支持以下两个通配符与 LIKE 操作符一起使用：

<table>
   <tr>
      <td>通配符</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>百分号（%）</td>
      <td>匹配一个或者多个字符。注意：MS Access 使用星号（*）作为匹配一个或者多个字符的通配符，而不是百分号（%）。</td>
   </tr>
   <tr>
      <td>下划线（_）</td>
      <td>匹配一个字符。注意：MS Access 使用问号（?），而不是下划线，来匹配任一字符。</td>
   </tr>
</table>

百分号代表零个、一个或者多个字符。下划线代表单一的字符。这些符号可以组合在一起使用。

## 语法： ##

“%” 和 “_” 的基本语法如下所示：

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

你可以用 AND 或 OR 操作符将多个条件合并在一起。这里，XXXX 可以为任何数值或者字符串。

## 示例： ##

<table>
   <tr>
      <td>语句</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '200%'</td>
      <td>找出任何以 200 开头的值。</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '%200%'</td>
      <td>找出任何存在 200 的值。</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '_00%'</td>
      <td>找出任何第二个位置和第三个位置为 0 的值。</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '2_%_%'</td>
      <td>找出任何以 2 开始，并且长度至少为 3 的值。</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '%2'</td>
      <td>找出任何以 2 结尾的值。</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '_2%3'</td>
      <td>找出任何第二个位置为 2，并且以 3 结束的值。</td>
   </tr>
   <tr>
      <td>WHERE SALARY LIKE '2___3'</td>
      <td>找出任何以 2 开始，以 3 结束的五位数。</td>
   </tr>
</table>

让我们来看一个真实的例子，考虑拥有如下记录的 CUSTOMERS 表：

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

下面的示例将会找到 CUSTOMER 表中所有 SALARY 以 200 开头的记录，并显示出来：

	SQL> SELECT * FROM CUSTOMERS
	WHERE SALARY LIKE '200%'; 

结果如下所示：

	+----+----------+-----+-----------+----------+
	| ID | NAME     | AGE | ADDRESS   | SALARY   |
	+----+----------+-----+-----------+----------+
	|  1 | Ramesh   |  32 | Ahmedabad |  2000.00 |
	|  3 | kaushik  |  23 | Kota      |  2000.00 |
	+----+----------+-----+-----------+----------+
