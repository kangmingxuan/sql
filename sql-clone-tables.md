# 克隆数据表 #

----------

有些情况下，你可能需要原样拷贝某张数据表。但是，CREATE TABEL 却不能满足你的需要，因为复制表必须和原表拥有一样的索引、默认值等等。

如果你在使用 MySQL 关系型数据库管理系统的话，下面几个步骤可以帮你解决这个问题：

- 使用 SHOW CREATE TABLE 命令来获取一条指定了原表的结构、索引等信息的 CREATE　TABLE 语句。
- 将语句中的表名修改为克隆表的名字，然后执行该语句。这样你就可以得到一张与原表完全相同的克隆表了。
- 如果你还想要复制表中的数据的话，请执行 INSERT INTO ...  SELECT 语句。

## 示例： ##

请尝试下面的示例，为 TUTORIALS_TBL 创建一张克隆表，其结构如下所示：

### 步骤一： ###

获取数据表的完整结构：

	SQL> SHOW CREATE TABLE TUTORIALS_TBL \G;
	*************************** 1. row ***************************
	       Table: TUTORIALS_TBL
	Create Table: CREATE TABLE `TUTORIALS_TBL` (
	  `tutorial_id` int(11) NOT NULL auto_increment,
	  `tutorial_title` varchar(100) NOT NULL default '',
	  `tutorial_author` varchar(40) NOT NULL default '',
	  `submission_date` date default NULL,
	  PRIMARY KEY  (`tutorial_id`),
	  UNIQUE KEY `AUTHOR_INDEX` (`tutorial_author`)
	) TYPE=MyISAM
	1 row in set (0.00 sec)

### 步骤二： ###

改变表名，创建新表：

	SQL> CREATE TABLE `CLONE_TBL` (
	  -> `tutorial_id` int(11) NOT NULL auto_increment,
	  -> `tutorial_title` varchar(100) NOT NULL default '',
	  -> `tutorial_author` varchar(40) NOT NULL default '',
	  -> `submission_date` date default NULL,
	  -> PRIMARY KEY  (`tutorial_id`),
	  -> UNIQUE KEY `AUTHOR_INDEX` (`tutorial_author`)
	-> ) TYPE=MyISAM;
	Query OK, 0 rows affected (1.80 sec)

### 步骤三： ###

执行完步骤二之后，数据库就会有克隆表了。如果你还想要复制旧表中的数据的话，可以执行 INSERT INTO... SELECT 语句。

	SQL> INSERT INTO CLONE_TBL (tutorial_id,
	    ->                        tutorial_title,
	    ->                        tutorial_author,
	    ->                        submission_date)
	    -> SELECT tutorial_id,tutorial_title,
	    ->        tutorial_author,submission_date,
	    -> FROM TUTORIALS_TBL;
	Query OK, 3 rows affected (0.07 sec)
	Records: 3  Duplicates: 0  Warnings: 0

最终，你将如期拥有一张完全相同的克隆表。