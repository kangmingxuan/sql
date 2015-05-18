# 操作符 #

---

每个操作符都是一个保留字，主要用于在 SQL 语句的 WHERE 子句中执行各种操作，例如比较和算术运算等。

操作符在 SQL 语句中指定了条件，并可以将同一语句中的不同条件连接起来。

- 算术运算符
- 比较运算符
- 逻辑运算符
- 用于否定条件的运算符

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
