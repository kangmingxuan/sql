# 约束 #

----------

约束是作用于数据表中列上的规则，用于限制表中数据的类型。约束的存在保证了数据库中数据的精确性和可靠性。

约束有列级和表级之分，列级约束作用于单一的列，而表级约束作用于整张数据表。

下面是 SQL 中常用的约束，这些约束虽然已经在[关系型数据库管理系统概念](sql-rdbms-concepts.md)一章中讨论过了，但是仍然值得在这里回顾一遍。

- [NOT NULL 约束](sql-not-null.htm)：保证列中数据不能有 NULL 值
- [DEFAULT 约束](/sql-default.htm)：提供该列数据未指定时所采用的默认值
- [UNIQUE 约束](sql-unique.htm)：保证列中的所有数据各不相同
- [主键约束](sql-primary-key.htm)：唯一标识数据表中的行/记录
- [外键约束](sql-foreign-key.htm)：唯一标识其他表中的一条行/记录
- [CHECK 约束](sql-check.htm)：此约束保证列中的所有值满足某一条件
- [索引](sql-index.htm)：用于在数据库中快速创建或检索数据

约束可以在使用 CREATE TABLE 创建表的时候指定，也可以在表创建之后由 ALTER TABLE 设置。

## 删除约束 ##

任何现有约束都可以通过在 ALTER TABLE 命令中指定 DROP CONSTRAINT 选项的方法删除掉。

例如，要去除 EMPLOYEES 表中的主键约束，可以使用下述命令：

    ALTER TABLE EMPLOYEES DROP CONSTRAINT EMPLOYEES_PK;

一些数据库实现可能提供了删除特定约束的快捷方法。例如，要在 Oracle 中删除一张表的主键约束，可以使用如下命令：

    ALTER TABLE EMPLOYEES DROP PRIMARY KEY;

某些数据库实现允许禁用约束。这样与其从数据库中永久删除约束，你可以只是临时禁用掉它，过一段时间后再重新启用。

## 完整性约束 ##

完整性约束用于保证关系型数据库中数据的精确性和一致性。对于关系型数据库来说，数据完整性由参照完整性（referential integrity，RI）来保证。

有很多种约束可以起到参照完整性的作用，这些约束包括主键约束（Primary Key）、外键约束（Foreign Key）、唯一性约束（Unique Constraint）以及上面提到的其他约束。