# MySQL

[TOC]

<!-- toc -->

---



## 一些小技巧

mysql小数取整：round函数

编码转化： `convert(name using utf8)` ，使用utf8编码name



执行sql文件

```bash
source xx.sql # 相对于运行mysql时的路径
```



查找特定表或列：

```mysql
# 在所有数据库中查找某张表
select table_name, table_schema as dbname from information_schema.tables where table_name='??';

# 在所有数据库中查找某个字段
select table_schema, table_name, column_name from information_schema.columns where column_name='name';
```



日期转换：

|          |                  date                   |          int(时间戳)           |                 str                 |
| :------: | :-------------------------------------: | :----------------------------: | :---------------------------------: |
| **date** |                    \                    |    `UNIX_TIMESTAMP(NOW())`     |  `DATE_FORMAT(NOW(), '%Y-%m-%d')`   |
| **int**  |       `FROM_UNIXTIME(1557733871)`       |               \                | `FROM_UNIXTIME(1451997924,'%Y-%d')` |
| **str**  | `STR_TO_DATE('2016-01-02', '%Y-%m-%d')` | `UNIX_TIMESTAMP('2016-01-02')` |                  \                  |



pager用法：实际上等于将它设置以后的所有mysql操作命令的输出通过pager设置命令执行，类似于管道符的作用。

`pager linux_bash_cmd`

nopager命令：取消pager设置，恢复之前的输出状态。（如果不设置nopager，那么只能通过重启mysql服务才能恢复了）



ubuntu下mysql不显示当前数据库名称：

```python
# 短期生效：执行mysql命令时添加下面参数
--prompt="\u(\d) >"

# 长期生效：修改配置my.cnf，然后重启mysql
[mysql]
default-character-set = utf8
prompt = MariaDB <\u> [\d] >
```





## 基础知识

登陆mysql：`mysql -h127.0.0.1 -P3306 -uroot -ppassword`

字符串相似查询： `where name like "%xxx%" ;`

数据类型：

* date ： `YYYY-mm-dd`
* datetime ： `YYYY-mm-dd HH:II:SS`

注释：

* `# comment`
* `-- comment`
* `/* comment \n comment */`



show 的用法：

* `show create table xxx;` : 查看创建table的语句
* `show [full] processlist` : 查看当前mysql的连接（不加full只显示前100条）。 `kill id` 可以终止连接
* `show index  from xxx` : 显示xxx的索引信息。
* `desc xxx` ： 显示table的所有字段
* `show grants` : 查看当前用户的所有权限

## 字符串操作

以下index均从1开始

* `left(str,index)` : 从左边第index开始截取
* `right(str,index)` : 从右边第index开始截取
* `substr(str,index)` : 当index>0从左边开始截取直到结束；当index<0从右边开始截取直到结束；当index=0返回空
* `substr(str,index,len)` : 截取str,从index开始，截取len长度。



字符串长度： `char_length(str)` ，



查找全是数字的字符串： `select * from sns5 where username regexp '^[0-9]+$' ;`







## 类型转换

字符串 -> 数字：

* 在字符串后加0：`'123'+0`
* cast函数： `cast('5.43' as decimal(50,15))`, `cast('555' as signed)`
* convert函数 ：`convert('1243', signed)`

数字 -> 字符串：

* convert函数 ：`convert(1243, char)`

## mysqldump：数据库备份

```bash
# 将dbname备份到backdb.sql中
mysqldump -uroot -hhost -p dbname > backdb.sql

# 备份数据表tb_1, tb_2
mysqldump -u root -h host -p dbname tb_1 tb_2 > backdb.sql

# 备份多个数据库
mysqldump -u root -h host -p --databases dbname1 dbname2 > backdb.sql

# 恢复数据
mysql -u root –password=root密码 数据库名 < 备份文件.sql

# 只dump数据表（没有数据）， 并将AUTO_INCREMENT去除
mysqldump -h 127.0.0.1 -u username -p --no-data -B db | sed 's/AUTO_INCREMENT\s*=\s*[0-9]*\s//g' > db.sql
```

其他参数：

* `-d` / `--no-data`：不dump数据，只dump表结构
* `-B db1 db2 ...` / `--databases db1 db2 ...`：dump多个数据库



MySQL查询结果保存到本地：

```bash
# 这是1条命令
mysql -h<公网IP> -P<端口号> -u<用户名> -p<密码> -D<指定数据库> >local.sql <<EOF
select * from table_name
EOF


mysql -h<公网IP> -P<端口号> -u<用户名> -p<密码> -D<指定数据库> --execute "sql语句"
```



## oracle

以#号结尾的字段含义：group# 可以说成是 group 号，是group 的序列化

$号含义：

* `GV$` : 全局视图，针对多个实例环境。
* `V$` : 针对某个实例的视图。
* `X$` : 是GV$视图的数据来源，Oracle内部表。
* `GV_$` : 是GV$的同义词。
* `V_$` : 是V$的同义词。

执行 sql文件：`> @demo.sql`



在命令窗口输入 `sqlplus / as sysdba` 后回车，即可连接到Oracle。登录时，采用的是操作系统验证的方式，所以用户名/密码输与不输入是一样的。



## 坑点

在mysql中做字符串与数字的比较时，会自动从第一个非数字的字符开始截断，将截断点前的字符串转换为数字，继而进行比较。

## 自带数据库

mysql数据库服务器有三个数据库：

* `information_schema` : 保存mysql服务器所有数据库的信息。比如数据库的名、数据库的表、访问权限、数据库表的数据类型，数据库索引的信息等等。就是关于这个数据库的点点滴滴信息都存储在这个数据库中。
* `mysql` ：mysql数据库中的所有的信息表。
* `test` ：空的数据库，用于测试。



`information_schema` ：

* `character_sets` : 表中存储了这个数据库中可用字符集的信息。
* `collations` : 表中存储了关于各个字符集的对照信息。
* `collation_character_set_applicability` : 表中存储指明可用的校对字符集。
* **`columns` : 表中存储了表中的列信息。**
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
* **`schemata` : 提供了有关数据库的信息。**
* `schema_privileges` : 方案权限表，给出了方案权限的信息。
* `session_status` : 描述了有关服务器会话变量状态信息，它对应于显示有关会话状态的信息。
* `session_variables` : 提供有关服务器会话变量值信息，它对应于显示有关会话值的信息。
* `statistics` : 描述了表的索引信息。
* **`tables` : 给出了关于数据库中表的信息。**
* `table_constraints` : 给出了关于描述存在约束的表。
* `table_privileges` : 表权限，表给出了关于表权限的信息。该信息来源于mysql.tables_priv授权表.
* `triggers` : 表提供了关于触发程序的信息。
* `user_privileges` : 用户权限表，表给出了关于全程权限的信息。该信息来源于mysql.user授权表。
* `views` : 表给出了关于数据库中的视图的信息。




## mysqldump



```bash
# 只dump数据
mysqldump -h127.0.0.1 -P3306 -uroot -p --no-create-info --databases db_1 --tables table_1 --where='date=20220916' > dump.sql

# dump之后可以使用diff查看差别


# 不导出数据, 只导出表
mysqldump -uroot -proot --no-data --databases db1 >/tmp/db1.sql
```



* `--lock-tables=false`： 不锁表dump

* `mysqldump　-t　数据库名　-uroot　-p　>　xxx.sql`: 只dump数据，不dump结构。在数据表名前面加”-t“参数

* `-d` / `--no-data`：不dump数据，只dump表结构

* `-B db1 db2 ...` / `--databases db1 db2 ...`：dump多个数据库



## 日期相关函数

周日是1, 周一是2, 依次类推, 周六是7
```mysql
SELECT DAYOFWEEK('1998-02-03');

select dayofweek(str_to_date(''+20220217, '%Y%m%d'));
```



## 修改数据

```mysql
begin;
rollback;
commit;
```



## IF语句

```mysql
SELECT
    IF(1>0, IF(2>1, '真', '假'), '假')
FROM
    Table
```



```mysql
SELECT
    CASE 1
        WHEN 1 THEN '字段的值是1'
        WHEN 2 THEN '字段的值是2'
        ELSE '字段的值3'
    END
FROM
    Table
```



## 补0

这里就是查询user表中的ID卡号，不足8位的补零

```mysql
select lpad(IdcardNo, 8, 0) from user;
```



## 查看mysql版本

查看MySQL版本的四种方法
1、终端下直接使用mysql命令：`mysql -V`

2、同样在终端使用命令： `mysql --help | grep Distrib`

3、登陆mysql之后使用内置命令: `select version();`

4、使用mysql内置命令： `MariaDB [(none)]> status;`



## 常用命令

```bash
# 去掉AUTO_INCREMENT
cat xx.sql |sed 's/AUTO_INCREMENT\s*=\s*[0-9]*\s//g' > xx_new.sql
```



### 更好的mysql命令行工具：mycli

- **痛点**：

  - 一些好的可视化工具如navicat不允许使用
  - 原生的mysql 命令使用时，要select查询字段，要精准的是输入正确字段名称，很容易错



https://www.mycli.net/install



```bash
pip3 install mycli
pip install mycli==1.20.0
```




## 将mysql的查询结果保存到文件中

方法一：直接执行命令.

```mysql
select count(1) from table  into outfile '/tmp/test.xls';
```

这种方法经常遇到权限的问题。很多时候需要去整权限。

方法二：查询都自动写入文件

```mysql
pager cat > /tmp/test.txt
```

之后的所有查询结果都自动写入/tmp/test.txt’，并前后覆盖，在框口不再显示查询结果。

取消pager:

```mysql
nopager
```



方法三：跳出mysql, 直接使用命令行进行重定向

```bash
 mysql -h 127.0.0.1 -u root -p XXXX -P 3306 -e "select * from table"  > /tmp/test/txt
```























