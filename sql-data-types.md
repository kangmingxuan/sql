# 数据类型 #

----------

SQL 数据类型是一种属性，它指定了任何 SQL 对象中数据的类型。在 SQL 中，任意一个列、变量或者表达式都有其数据类型。

创建表的时候，你会用到这些数据类型。你应该根据需要为表中的每一个列选择合适的数据类型。

SQL Server 提供了六种数据类型供你使用：

## 精确数值数据类型： ##

<table>
   <tr>
      <td>数据类型</td>
      <td>下限</td>
      <td>上限</td>
   </tr>
   <tr>
      <td>bigint</td>
      <td>-9,223,372,036,854,770,000</td>
      <td>9,223,372,036,854,770,000</td>
   </tr>
   <tr>
      <td>int</td>
      <td>-2,147,483,648</td>
      <td>2,147,483,647</td>
   </tr>
   <tr>
      <td>smallint</td>
      <td>-32,768</td>
      <td>32,767</td>
   </tr>
   <tr>
      <td>tinyint</td>
      <td>0</td>
      <td>255</td>
   </tr>
   <tr>
      <td>bit</td>
      <td>0</td>
      <td>1</td>
   </tr>
   <tr>
      <td>decimal</td>
      <td>1E+38</td>
      <td>10^38 -1</td>
   </tr>
   <tr>
      <td>numeric</td>
      <td>1E+38</td>
      <td>10^38 -1</td>
   </tr>
   <tr>
      <td>money</td>
      <td>-922,337,203,685,477.00</td>
      <td>922,337,203,685,477.00</td>
   </tr>
   <tr>
      <td>smallmoney</td>
      <td>-214,748.36</td>
      <td>214,748.36</td>
   </tr>
</table>


## 近似数值数据类型 ##

<table>
   <tr>
      <td>数据类型</td>
      <td>下限</td>
      <td>上限</td>
   </tr>
   <tr>
      <td>float</td>
      <td>-1.79E + 308</td>
      <td>1.79E + 308</td>
   </tr>
   <tr>
      <td>real</td>
      <td>-3.40E + 38</td>
      <td>3.40E + 38</td>
   </tr>
   <tr>
      <td></td>
   </tr>
</table>

## 日期和时间数据类型 ##

<table>
   <tr>
      <td>数据类型</td>
      <td>下限</td>
      <td>上限</td>
   </tr>
   <tr>
      <td>datetime</td>
      <td>Jan 1, 1753</td>
      <td>31-Dec-99</td>
   </tr>
   <tr>
      <td>smalldatetime</td>
      <td>1-Jan-00</td>
      <td>6-Jun-79</td>
   </tr>
   <tr>
      <td>date</td>
      <td>存储一个日期数据，例如 June 30, 1991</td>
      <td></td>
   </tr>
   <tr>
      <td>time</td>
      <td>存储一个时间数据，例如 12:30 P.M.</td>
      <td></td>
   </tr>
</table>

**注意：**datetime 的时间和精度为 3.33 ms，而 smalldatetime 的时间精度为 1 min。

## 字符串数据类型 ##

<table>
   <tr>
      <td>数据类型</td>
      <td>下限</td>
      <td>上限</td>
   </tr>
   <tr>
      <td>char</td>
      <td>char</td>
      <td>最大长度为 8,000 字符。（定长非 Unicode 字符）</td>
   </tr>
   <tr>
      <td>varchar</td>
      <td>varchar</td>
      <td>最大长度为 8,000 字符。（变长非 Unicode 数据）</td>
   </tr>
   <tr>
      <td>varchar(max)</td>
      <td>varchar(max)</td>
      <td>最大长度为 231 字符, 变长非 Unicode 数据 (仅限 SQL Server 2005).</td>
   </tr>
   <tr>
      <td>text</td>
      <td>text</td>
      <td>变长非 Unicode 字符数据，最大长度 2,147,483,647 字符。</td>
   </tr>
</table>

## Unicode 字符串数据类型 ##

<table>
   <tr>
      <td>数据类型</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>nchar</td>
      <td>最大长度 4000 字符。（定长 Unicode 字符串）</td>
   </tr>
   <tr>
      <td>nvarchar</td>
      <td>最大长度 4000 字符。（变长 Unicode 字符串）</td>
   </tr>
   <tr>
      <td>nvarchar(max)</td>
      <td>最大长度 231 字符 。（仅限 SQL Server 2005）。（变长 Unicode 字符串）</td>
   </tr>
   <tr>
      <td>ntext</td>
      <td>最大长度 1,073,741,823 字符。（变长 Unicode 字符串）</td>
   </tr>
</table>

## 二进制数据类型 ##

<table>
   <tr>
      <td>数据类型</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>binary</td>
      <td>最大长度 8000 字节。（定长二进制数据）</td>
   </tr>
   <tr>
      <td>varbinary</td>
      <td>最大长度 8000 字节。（变长二进制数据）</td>
   </tr>
   <tr>
      <td>varbinary(max)</td>
      <td>最大长度 231字节 （仅限 SQLServer 2005）。 （变长二进制数据）</td>
   </tr>
   <tr>
      <td>image</td>
      <td>最大长度  2,147,483,647 字节。（变长二进制数据）</td>
   </tr>
</table>

## 其他数据类型 ##

<table>
   <tr>
      <td>数据类型</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>sql_variant</td>
      <td>存储多种 SQL 支持的数据类型，text、ntext、timestamp 除外。</td>
   </tr>
   <tr>
      <td>timestamp</td>
      <td>一个数据库级的唯一值，每当有行更新此数据就会更新。</td>
   </tr>
   <tr>
      <td>uniqueidentifier</td>
      <td>全局唯一标识符（GUID）</td>
   </tr>
   <tr>
      <td>xml</td>
      <td>存储 XML 数据。你可以在列或者变量中存储 XML 实例。（仅限 SQL Server 2005）</td>
   </tr>
   <tr>
      <td>cursor</td>
      <td>指向 cursor 对象。</td>
   </tr>
   <tr>
      <td>table</td>
      <td>存储结果，以备后用。</td>
   </tr>
</table>
