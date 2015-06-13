# 日期函数 #

----------

下面的列表中是 SQL 中所有与日期和时间相关的重要函数。你所用的 RDBMS 可能会支持更多其他的函数。下面的列表基于 MySQL 关系型数据库管理系统。

<table>
   <tr>
      <td>名称</td>
      <td>描述</td>
   </tr>
   <tr>
      <td>ADDDATE()</td>
      <td>增加日期</td>
   </tr>
   <tr>
      <td>ADDTIME()</td>
      <td>增加时间</td>
   </tr>
   <tr>
      <td>CONVERT_TZ()</td>
      <td>将当前时区更改为另一时区</td>
   </tr>
   <tr>
      <td>CURDATE()</td>
      <td>返回当前日期</td>
   </tr>
   <tr>
      <td>CURRENT_DATE(), CURRENT_DATE</td>
      <td>CURDATE() 的别名</td>
   </tr>
   <tr>
      <td>CURRENT_TIME(), CURRENT_TIME</td>
      <td>CURTIME() 的别名</td>
   </tr>
   <tr>
      <td>CURRENT_TIMESTAMP(), CURRENT_TIMESTAMP</td>
      <td>NOW() 的别名</td>
   </tr>
   <tr>
      <td>CURTIME()</td>
      <td>返回当前时间</td>
   </tr>
   <tr>
      <td>DATE_ADD()</td>
      <td>将两个日期相加</td>
   </tr>
   <tr>
      <td>DATE_FORMAT()</td>
      <td>按照指定格式格式化日期</td>
   </tr>
   <tr>
      <td>DATE_SUB()</td>
      <td>将两个日期相减</td>
   </tr>
   <tr>
      <td>DATE()</td>
      <td>从 date 或者 datetime 表达式中提取出日期部分</td>
   </tr>
   <tr>
      <td>DATEDIFF()</td>
      <td>将两个日期相减</td>
   </tr>
   <tr>
      <td>DAY()</td>
      <td>DAYOFMONTH() 的别名</td>
   </tr>
   <tr>
      <td>DAYNAME()</td>
      <td>返回某天在用星期中的名称</td>
   </tr>
   <tr>
      <td>DAYOFMONTH()</td>
      <td>返回某天是当月的第几天 （1-31）</td>
   </tr>
   <tr>
      <td>DAYOFWEEK()</td>
      <td>返回某天是该星期的第几天</td>
   </tr>
   <tr>
      <td>DAYOFYEAR()</td>
      <td>返回某天是一年中的第几天（1-366）</td>
   </tr>
   <tr>
      <td>EXTRACT</td>
      <td>提取日期中的某一部分</td>
   </tr>
   <tr>
      <td>FROM_DAYS()</td>
      <td>将天数转换为日期</td>
   </tr>
   <tr>
      <td>FROM_UNIXTIME()</td>
      <td>将某个日期格式化为 UNIX 时间戳</td>
   </tr>
   <tr>
      <td>HOUR()</td>
      <td>提取小时</td>
   </tr>
   <tr>
      <td>LAST_DAY</td>
      <td>返回参数日期所在月份的最后一天</td>
   </tr>
   <tr>
      <td>LOCALTIME(), LOCALTIME</td>
      <td>NOW() 的别名</td>
   </tr>
   <tr>
      <td>LOCALTIMESTAMP, LOCALTIMESTAMP()</td>
      <td>NOW() 的别名</td>
   </tr>
   <tr>
      <td>MAKEDATE()</td>
      <td>利用年份和某天在该年所处的天数来创建日期</td>
   </tr>
   <tr>
      <td>MAKETIME</td>
      <td>MAKETIME()</td>
   </tr>
   <tr>
      <td>MICROSECOND()</td>
      <td>由参数返回微秒</td>
   </tr>
   <tr>
      <td>MINUTE()</td>
      <td>由参数返回分钟</td>
   </tr>
   <tr>
      <td>MONTH()</td>
      <td>返回日期参数的月份</td>
   </tr>
   <tr>
      <td>MONTHNAME()</td>
      <td>返回月份的名字</td>
   </tr>
   <tr>
      <td>NOW()</td>
      <td>返回当前日期和时间</td>
   </tr>
   <tr>
      <td>PERIOD_ADD()</td>
      <td>向年月格式的日期数据之间添加一段时间</td>
   </tr>
   <tr>
      <td>PERIOD_DIFF()</td>
      <td>返回两个年月格式的日期数据之间的月份数</td>
   </tr>
   <tr>
      <td>QUARTER()</td>
      <td>返回日期参数所在的季度</td>
   </tr>
   <tr>
      <td>SEC_TO_TIME()</td>
      <td>将秒数转换为 'HH:MM:SS' 格式</td>
   </tr>
   <tr>
      <td>SECOND()</td>
      <td>返回参数中的秒数 (0-59)</td>
   </tr>
   <tr>
      <td>STR_TO_DATE()</td>
      <td>将字符串转换为日期数据</td>
   </tr>
   <tr>
      <td>SUBDATE()</td>
      <td>以三个参数调用的时候是 DATE_SUB() 的同义词</td>
   </tr>
   <tr>
      <td>SUBTIME()</td>
      <td>减去时间</td>
   </tr>
   <tr>
      <td>SYSDATE()</td>
      <td>返回函数执行的时的时刻</td>
   </tr>
   <tr>
      <td>TIME_FORMAT()</td>
      <td>格式化时间</td>
   </tr>
   <tr>
      <td>TIME_TO_SEC()</td>
      <td>将时间参数转换为秒数</td>
   </tr>
   <tr>
      <td>TIME()</td>
      <td>返回参数表达式中的时间部分</td>
   </tr>
   <tr>
      <td>TIMEDIFF()</td>
      <td>将两个时间相减</td>
   </tr>
   <tr>
      <td>TIMESTAMP()</td>
      <td>只有一个参数时，该函数返回 date 或者 datetime 表达式。当有两个参数时，将两个参数相加。</td>
   </tr>
   <tr>
      <td>TIMESTAMPADD()</td>
      <td>在 datetime 表达式上加上一段时间</td>
   </tr>
   <tr>
      <td>TIMESTAMPDIFF()</td>
      <td>在 datetime 表达式上减去一段时间</td>
   </tr>
   <tr>
      <td>TO_DAYS()</td>
      <td>将日期参数转换为天数</td>
   </tr>
   <tr>
      <td>UNIX_TIMESTAMP()</td>
      <td>返回 UNIX 时间戳</td>
   </tr>
   <tr>
      <td>UTC_DATE()</td>
      <td>返回当前 UTC 日期</td>
   </tr>
   <tr>
      <td>UTC_TIME()</td>
      <td>返回当前 UTC 时间</td>
   </tr>
   <tr>
      <td>UTC_TIMESTAMP()</td>
      <td>返回当前 UTC 日期和时间</td>
   </tr>
   <tr>
      <td>WEEK()</td>
      <td>返回参数的星期数</td>
   </tr>
   <tr>
      <td>WEEKDAY()</td>
      <td>返回日期参数时一个星期中的第几天</td>
   </tr>
   <tr>
      <td>WEEKOFYEAR()</td>
      <td>返回日期参数是日历上的第几周 (1-53)</td>
   </tr>
   <tr>
      <td>YEAR()</td>
      <td>返回日期参数中的年份</td>
   </tr>
   <tr>
      <td>YEARWEEK()</td>
      <td>返回年份和星期</td>
   </tr>
</table>