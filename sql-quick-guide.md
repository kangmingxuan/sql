# 快速指南 #

----------

## 什么是 SQL？##

SQL 是结构化查询语言（Structured Query Language），一种用于存储、操作或者检索存储在关系型数据库中数据的计算机语言。

SQL 是关系型数据库系统（Relation Database System）的标准语言。所有的关系型数据库管理系统，例如 MySQL、MS Access、Oracle、Sybase、Informix、Postgres SQL和SQL Server，都使用 SQL 作为其标准数据库语言。

当然，它们用的都是不同的 SQL 方言。例如：

- 微软的 SQL Server 使用的是 T-SQL
- Oracle 使用的是 PL/SQL
- 微软的 Access 中的 SQL 叫做 JET SQL （本地格式）等等

## 为什么要用 SQL？ ##

- 允许用户访问关系型数据库中的数据
- 允许用户对数据做出描述
- 允许用于定义数据库中的数据，并对其进行操作
- 允许通过 SQL 模块、库或者预编译器的等方式，嵌入到其他语言中
- 允许用户创建或删除数据库和表
- 允许用户在数据库中创建视图、存储过程和函数
- 允许用户对表、过程和视图设进行权限设置

## 什么是关系型数据库管理系统？ ##

RDBMS 是关系型数据库管理系统（**R**elational **D**ata**B**ase **M**anagement **S**ystem)的缩写，它是 SQL 以及所有现代数据库系统，例如 MS SQL Server、IBM DB2、Oracle、MySQL 和 MS Access等的基础。

关系型数据库管理系统（RDBMS）是一种基于 E.F. 科德提出的关系模型的数据库管理系统。

## 什么是表？ ##

RDBMS 中的数据存储在被称作**表**的数据库对象中。表是相互关联的数据记录的集合，由一系列的行和列组成。

谨记，表是关系型数据库中最常见也是最简单的数据存储形式。

## 什么是字段？ ##

每张表都能够划分成更小的实体——**字段**。例如，客户信息表中有 ID、NAME、AGE、ADDRESS 和 SALARY 五个字段。

一个字段限定了数据表中的列，被用来维护表中所有记录的特定信息。

## 什么是记录或者数据行？ ##

**记录**或者说数据**行**是存在于数据表中的独立条目。

记录就是表中水平排列的数据构成的实体。

## 什么是列？ ##

**列**是表中竖直排列的实体，它包含了表中与某一特定字段相关的所有信息。

## 什么是 NULL 值？ ##

NULL 值是表中以空白形式出现的值，表示该记录在此字段处没有设值。

一定要明白 NULL 值同 0 值或者包含空格的字段是不同的。值为 NULL 的字段是在记录创建的时候就被留空的字段。

## SQL 约束 ##

约束是表中的数据列必须遵守的规则，用于限制表中数据的类型。约束保证了数据库中数据的精确性和可靠性。

约束可以列级和表级。列级的约束只限制单一的列，而表级的约束作用于整个表。

## 语法 ##

SQL 遵循一组称为“语法”的规则和指南。本教程列出了所有的 SQL 基础语法供你快速学习 SQL 之用。

所有的 SQL 语句都以下列关键字之一开始：SELECT、INSERT、UPDATE、DELETE、ALTER、DROP、CREATE、USE、SHOW，并以一个分号（;）结束。

有一点需要特别注意：SQL **不区分大小写**，也就是说 SELECT 和 select 在 SQL 语句中有相同的含义。然而，MySQL 在表的名称方面并不遵循此规定。所以，如果你在使用 MySQL 的话，你需要在程序中严格按照它们在数据库中名字进行使用。

## SQL SELECT 语句 ##

    SELECT column1, column2....columnN
    FROM   table_name;

## SQL DISTINCT 子句 ##

    SELECT DISTINCT column1, column2....columnN
    FROM   table_name;

## SQL WHERE 子句 ##

    SELECT column1, column2....columnN
    FROM   table_name
    WHERE  CONDITION;

## SQL AND/OR 子句 ##
    
    SELECT column1, column2....columnN
    FROM   table_name
    WHERE  CONDITION-1 {AND|OR} CONDITION-2;

## SQL IN 子句 ##

    SELECT column1, column2....columnN
    FROM   table_name
    WHERE  column_name IN (val-1, val-2,...val-N);

## SQL BETWEEN 子句 ##

    SELECT column1, column2....columnN
    FROM   table_name
    WHERE  column_name BETWEEN val-1 AND val-2;

## SQL LIKE 子句 ##

    SELECT column1, column2....columnN
    FROM   table_name
    WHERE  column_name LIKE { PATTERN };

## SQL ORDER BY 子句 ##

    SELECT column1, column2....columnN
    FROM   table_name
    WHERE  CONDITION
    ORDER BY column_name {ASC|DESC};

## SQL GROUP BY 子句 ##

    SELECT SUM(column_name)
    FROM   table_name
    WHERE  CONDITION
    GROUP BY column_name;

## SQL COUNT 子句 ##

    SELECT COUNT(column_name)
    FROM   table_name
    WHERE  CONDITION;

## SQL HAVING 子句 ##

    SELECT SUM(column_name)
    FROM   table_name
    WHERE  CONDITION
    GROUP BY column_name
    HAVING (arithematic function condition);

## SQL CREATE TABLE 语句 ##

    CREATE TABLE table_name(
    column1 datatype,
    column2 datatype,
    column3 datatype,
    .....
    columnN datatype,
    PRIMARY KEY( one or more columns )
    );

## SQL DROP TABLE 语句 ##

    DROP TABLE table_name;

## SQL CREATE INDEX 语句 ##

    CREATE UNIQUE INDEX index_name
    ON table_name ( column1, column2,...columnN);

## SQL DROP INDEX 语句 ##

    ALTER TABLE table_name
    DROP INDEX index_name;

## SQL DESC 语句 ##

    DESC table_name;

## SQL TRUNCATE TABLE 语句 ##

    TRUNCATE TABLE table_name;

## SQL ALTER TABLE 语句（重命名）##

    ALTER TABLE table_name RENAME TO new_table_name;

## SQL INSERT INTO 语句 ##

    INSERT INTO table_name( column1, column2....columnN)
    VALUES ( value1, value2....valueN);

## SQL UPDATE 语句 ##
    
    UPDATE table_name
    SET column1 = value1, column2 = value2....columnN=valueN
    [ WHERE  CONDITION ];

## SQL DELETE 语句 ##

    DELETE FROM table_name
    WHERE  {CONDITION};

## SQL CREATE DATABASE 语句 ##

    CREATE DATABASE database_name;

## SQL DROP DATABASE 语句 ##

    DROP DATABASE database_name;

## SQL USE 语句 ##

    USE database_name;

## SQL COMMIT 语句 ##

    COMMIT;

## SQL ROLLBACK 语句 ##

    ROLLBACK;

## SQL 运算符： ##

## SQL 算术运算符 ##

假设变量 a 的值为 10， 变量 b 的值为 20，那么：

[查看示例](sql-arithmetic-operators.htm)

<table>
   <tr>
      <td>操作符</td>
      <td>描述</td>
      <td>示例</td>
   </tr>
   <tr>
      <td>+</td>
      <td>相加：将符号两边的数值加起来。</td>
      <td>a + b 得 30</td>
   </tr>
   <tr>
      <td>-</td>
      <td>相减：从最边的操作数中减去右边的操作数。</td>
      <td>a - b 得 -10</td>
   </tr>
   <tr>
      <td>*</td>
      <td>相乘：将两边的操作数相乘。</td>
      <td>a * b 得 200</td>
   </tr>
   <tr>
      <td>/</td>
      <td>相除：用右边的操作数除以左边的操作数。</td>
      <td>b / a 得 2</td>
   </tr>
   <tr>
      <td>%</td>
      <td>取余：用右边的操作数除以左边的操作数，并返回余数。</td>
      <td>b % a 得 0</td>
   </tr>
</table>

## SQL 比较运算符 ##

假设变量 a 的值为 10， 变量 b 的值为 20，那么：

[查看示例](sql-comparison-operators.htm)

<table>
   <tr>
      <td>操作符</td>
      <td>描述</td>
      <td>示例</td>
   </tr>
   <tr>
      <td>=</td>
      <td>检查两个操作数的值是否相等，是的话返回 true。</td>
      <td>(a = b) 不为 true。</td>
   </tr>
   <tr>
      <td>!=</td>
      <td>检查两个操作数的值是否相等，如果不等则返回 true。</td>
      <td>(a != b) 为 true。</td>
   </tr>
   <tr>
      <td><></td>
      <td>检查两个操作数的值是否相等，如果不等则返回 true。</td>
      <td>(a <> b) 为真。</td>
   </tr>
   <tr>
      <td>></td>
      <td>检查左边的操作数是否大于右边的操作数，是的话返回真。</td>
      <td>(a > b) 不为 true。</td>
   </tr>
   <tr>
      <td><</td>
      <td>检查左边的操作数是否小于右边的操作数，是的话返回真。</td>
      <td>(a < b) 为 true。</td>
   </tr>
   <tr>
      <td>>=</td>
      <td>检查左边的操作数是否大于或等于右边的操作数，是的话返回真。</td>
      <td>(a >= b) 不为 true。</td>
   </tr>
   <tr>
      <td><=</td>
      <td>检查左边的操作数是否小于或等于右边的操作数，是的话返回真。</td>
      <td>(a <= b) 为 true。</td>
   </tr>
   <tr>
      <td>!<</td>
      <td>检查左边的操作数是否不小于右边的操作数，是的话返回真。</td>
      <td>(a !< b) 为 false。</td>
   </tr>
   <tr>
      <td>!></td>
      <td>检查左边的操作数是否不大于右边的操作数，是的话返回真。</td>
      <td>(a !> b) 为 true。</td>
   </tr>
</table>

## SQL 逻辑运算符 ##

下面列出了 SQL 中可用的逻辑运算符。

[查看示例](sql-logical-operators.htm)


<table>
   <tr>
      <td>运算符</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>ALL</td>
      <td>ALL 运算符用于将一个值同另一个值集中所有的值进行比较。</td>
   </tr>
   <tr>
      <td>AND</td>
      <td>AND 运算符使得在 WHERE 子句中可以同时存在多个条件。</td>
   </tr>
   <tr>
      <td>ANY</td>
      <td>ANY 运算符用于将一个值同条件所指定的列表中的任意值相比较。</td>
   </tr>
   <tr>
      <td>BETWEEN</td>
      <td>给定最小值和最大值，BETWEEN 运算符可以用于搜索区间内的值。</td>
   </tr>
   <tr>
      <td>EXISTS</td>
      <td>EXISTS 运算符用于在表中搜索符合特定条件的行。</td>
   </tr>
   <tr>
      <td>IN</td>
      <td>IN 运算符用于将某个值同指定的一列字面值相比较。</td>
   </tr>
   <tr>
      <td>LIKE</td>
      <td>LIKE 运算符用于使用通配符对某个值和与其相似的值做出比较。</td>
   </tr>
   <tr>
      <td>NOT</td>
      <td>NOT 操作符反转它所作用的操作符的意义。例如，NOT EXISTS、NOT BETWEEN、NOT IN 等。这是一个求反运算符。</td>
   </tr>
   <tr>
      <td>OR</td>
      <td>OR 运算符用于在 SQL 语句中连接多个条件。</td>
   </tr>
   <tr>
      <td>IS NULL</td>
      <td>NULL Operator 用于将某个值同 NULL 作比较。</td>
   </tr>
   <tr>
      <td>UNIQUE</td>
      <td>UNIQUE 运算符检查指定表的所有行，以确定没有重复。</td>
   </tr>
</table>

## 一些有用的函数 ##

SQL 有很多内置函数，用于处理字符串或者数值型数据。下面是所有这些有用的内置函数的列表：

- SQL COUNT 函数：COUNT 是一个聚集函数，用于统计数据表中数据的行数。
- SQL MAX 函数：MAX 是一个聚集函数，使得我们可以获取指定列中的最大值。
- SQL MIN 函数：MIN 是一个聚集函数，使得我们可以获取指定列中的最小值。
- SQL AVG 函数：AVG 是一个聚集函数，用于统计指定列的平均值。
- SQL SUM 函数：SUM 是一个聚集函数，用于统计数值型列的总和。
- SQL SQRT 函数：计算给定值的平方根。
- SQL RAND 函数：用 SQL 命令来产生随机数。
- SQL CONCAT 函数：用于在 SQL 命令中连接字符串。
- SQL Numeric 函数：列出 SQL 中所有用于操纵数值的函数。
- SQL String 函数：列出 SQL 中所有用于操纵字符串的函数。