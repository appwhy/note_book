# MySQL

[TOC]

<!-- toc -->

---

## 自带数据库

mysql数据库服务器有三个数据库：

* `information_schema` : 保存mysql服务器所有数据库的信息。比如数据库的名、数据库的表、访问权限、数据库表的数据类型，数据库索引的信息等等。就是关于这个数据库的点点滴滴信息都存储在这个数据库中。
* `mysql` ：mysql数据库中的所有的信息表。
* `test` ：空的数据库，用于测试。



`information_schema` ：

* `character_sets` : 表中存储了这个数据库中可用字符集的信息。
* `collations` : 表中存储了关于各个字符集的对照信息。
* `collation_character_set_applicability` : 表中存储指明可用的校对字符集。
* `columns` : 表中存储了表中的列信息。
* `column_privileges` : 表中存储了关于列权限的信息。这个表中的信息来自mysql.columns_priv的授权表。
* `engines` : 这个表中是关于存储引擎信息。
* `events` : 这个表中是关于数据库中事件规则的信息。
* `files` : 这个表中提供了mysql表空间存储的有关文件信息。
* `global_status` : 提供有关服务器状态变量的信息，它对应于显示全局状态信息表。
* `global_variables` : 提供有关服务器全局变量值的信息，提供全局变量的值。
* `key_column_usage` : 描述了具有约束的键列。
* `partitions` : 分区表提供有关分区的信息。
* `plugins` : 描述了数据库的有关插件信息。
* `processlist` : 描述了数据库有关进程信息的表。
* `profiling` : 分析表描述了语句分析信息；其内容对应于显示配置文件生成的信息并显示配置文件。
* `referential_constraints` : 描述了外键的约束信息，可以查看外键约束。
* `routines` : 这个表提供了存储子程序(存储程序和函数)的信息。此时，routines表不包含自定义函数(udf)。名为“mysql.proc name”的列指明了对应于information_schema.routines表的mysql.proc表列，如果有的话。
* `schemata` : 提供了有关数据库的信息。
* `schema_privileges` : 方案权限表，给出了方案权限的信息。
* `session_status` : 描述了有关服务器会话变量状态信息，它对应于显示有关会话状态的信息。
* `session_variables` : 提供有关服务器会话变量值信息，它对应于显示有关会话值的信息。
* `statistics` : 描述了表的索引信息。
* `tables` : 给出了关于数据库中表的信息。
* `table_constraints` : 给出了关于描述存在约束的表。
* `table_privileges` : 表权限，表给出了关于表权限的信息。该信息来源于mysql.tables_priv授权表.
* `triggers` : 表提供了关于触发程序的信息。
* `user_privileges` : 用户权限表，表给出了关于全程权限的信息。该信息来源于mysql.user授权表。
* `views` : 表给出了关于数据库中的视图的信息。