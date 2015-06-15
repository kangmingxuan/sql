# 注入 #

----------

如果你从网页中获取用户输入，并将其插入到 SQL 数据库中的话，那么你很可能已经暴露于一种被称作 **SQL 注入**的安全风险之下了。

本节将会教你如何防止 SQL 注入，以及如何保护 Perl 这样的服务器端脚本中的程序和 SQL 语句。


注入通常发生在获取用户输入的时候，例如预期得到用户的名字，但是得到的却是一段很可能会在你不知情的情况下运行的 SQL 语句。

绝对不要相信用户提供的数据，处理这些数据之前必须进行验证；通常，验证工作由模式匹配来完成。

下面的例子中，**name** 仅限由字母、数字和下划线组成，并且长度在 8 到 20 之间（你可以根据需要修改这些规则）。

	if (preg_match("/^\w{8,20}$/", $_GET['username'], $matches))
	{
	   $result = mysql_query("SELECT * FROM CUSTOMERS 
	                          WHERE name=$matches[0]");
	}
	else 
	{
	   echo "user name not accepted";
	}

为了展示问题所在，请考虑下面这段代码：

	// supposed input
	$name = "Qadir'; DELETE FROM CUSTOMERS;";
	mysql_query("SELECT * FROM CUSTOMSRS WHERE name='{$name}'");

下面的函数调用本来是要从 CUSTOMERS 表中取得 name 字段与用户给定的输入相匹配的记录。通常情况下，$name 只包含字母和数字，或许还有空格，例如字符串 ilia。但是，这里通过在 $name 上附加一段全新的查询语句，将原有的函数调用变为了数据库的灾难：注入的 DELETE 语句将会删除表中所有的记录。

幸运的是，如果你在使用　MySQL 的话，mysql_query() 函数不允许查询堆积（query stacking），或者说在一次函数调用中执行多次 SQL 查询。如果你试图进行堆积式查询的话，函数调用将会失败。

然而，其他的 PHP 数据库扩展，例如 SQLite 和 PostgreSQL 会愉快地接受堆积式查询，执行字符串中所有的查询，并由此产生严重的安全问题。

## 阻止 SQL 注入： ##

你可以在 Perl 或者 PHP 等脚本语言中巧妙地处理所有的转义字符。PHP 的 MySQL 扩展提供了一个 mysql_real_escape_string() 函数，来转义那些对 MySQL 有特殊意义的字符。

	if (get_magic_quotes_gpc()) 
	{
	  $name = stripslashes($name);
	}
	$name = mysql_real_escape_string($name);
	mysql_query("SELECT * FROM CUSTOMERS WHERE name='{$name}'");

## LIKE 困境： ##

要破解 LIKE 困境，必须有一种专门的转义机制，将用户提供的 '%' 和 '_' 转换为字面值。为此你可以使用 addcslashes() 函数，该函数允许指定要进行转义的字符的范围。

	$sub = addcslashes(mysql_real_escape_string("%str"), "%_");
	// $sub == \%str\_
	mysql_query("SELECT * FROM messages 
	             WHERE subject LIKE '{$sub}%'");

