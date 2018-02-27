# SQL
- SQL学习基础教程: http://www.runoob.com/sql/sql-tutorial.html
- SQL快速参考：http://www.runoob.com/sql/sql-quickref.html

# SQL 是什么？
- 结构化查询语言，全称是 Structured Query Language
- 访问和处理数据库

# 在网站中使用 SQL
- 要创建一个显示数据库中数据的网站，您需要：
- RDBMS(关系型数据库管理系统) 数据库程序（比如 MS Access、SQL Server、MySQL）
- 使用服务器端脚本语言，比如 PHP 或 ASP
- 使用 SQL 来获取您想要的数据
- 使用 HTML / CSS

# 数据库表，一个直观的例子
 一个数据库通常包含一个或多个表。每个表由一个名字标识（例如:"Websites"）,表包含带有数据的记录（行）。
 在 MySQL 的 RUNOOB 数据库中创建了 Websites 表，用于存储网站记录。
- mysql> use RUNOOB;
- mysql> set names utf8;
- mysql> SELECT * FROM Websites;

```
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝         | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程     | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博         | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+
```
**解析**
 - use RUNOOB：选择数据库
 - set names utf8：用于设置使用的字符集，字符集中可以出现中文
 - SELECT * FROM Websites： 读取数据表的信息

# 一些最重要的 SQL 命令
- **SELECT** - 从数据库中提取数据
- **UPDATE** - 更新数据库中的数据
- **DELETE** - 从数据库中删除数据
- **INSERT INTO** - 向数据库中插入新数据
- **CREATE DATABASE** - 创建新数据库
- **ALTER DATABASE** - 修改数据库
- **CREATE TABLE** - 创建新表
- **ALTER TABLE** - 变更（改变）数据库表
- **DROP TABLE** - 删除表
- **CREATE INDEX** - 创建索引（搜索键）
- **DROP INDEX** - 删除索引

# 分类演示
```
使用RUNOOB样本数据库的Websites表

SELECT：
SELECT name,country
FROM Websites；

SELECT DISTINCT:
DISTINCT 用于返回唯一不同的值
SELECT DISTINCT country FROM Websites;
```

```
WHERE:
用于提取满足指定标准的记录

GRAMMAR
SELECT column_name,column_name
FROM table_name
WHERE column_name operator value;

EXAMPLES
SELECT * FROM Websites
WHERE country = 'CN';
and
SELECT * FROM Websites
WHERE id = 1;

逻辑运算的优先级：
() > not > and > or

空值判断： is null
Select * from emp where comm is null;

between and (在...之间的值):
Select * from emp where sal between 1500 and 3000;
注意：大于等于 1500 且小于等于 3000， 1500 为下限，3000 为上限，下限在前，上限在后，查询的范围包涵有上下限的值。

In:
Select * from emp where sal in (5000,3000,1500);
查询 EMP 表 SAL 列中等于 5000，3000，1500 的值。

like:
Like模糊查询
Select * from emp where ename like 'M%';
查询 EMP 表中 Ename 列中有 M 的值，M 为要查询内容中的模糊信息。
 % 表示多个字值，_ 下划线表示一个字符；
 M% : 为能配符，正则表达式，表示的意思为模糊查询信息为 M 开头的。
 %M% : 表示查询包含M的所有内容。
 %M_ : 表示查询以M在倒数第二位的所有内容。
 
WHERE子句并不一定带比较运算符，当不带运算符时，会执行一个隐式转换。当0时转化为 false，当其他值是转化为true。例如：
SELECT studentNO FROM student WHERE 0
则会返回一个空集，因为每一行记录WHERE都返回false。

SELECT  studentNO  FROM student WHERE 1;
或者
SELECT studentNO FROM student WHERE 'abc';
都将返回student表所有行记录的studentNO列。因为每一行记录WHERE都返回true。

AND & OR:
如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录。
如果第一个条件和第二个条件中只要有一个成立，则 OR 运算符显示一条记录。

实例
从 "Websites" 表中选取 alexa 排名大于 "15" 且国家为 "CN" 或 "USA" 的所有网站：
SELECT * FROM Websites
WHERE alexa > 15
AND (country = 'CN' OR country = 'USA');
```

```
ORDER BY:
关键字用于对结果集按照一个列或者多个列进行排序。

关键字默认按照升序对记录进行排序,如果需要按照降序对记录进行排序，可以使用 DESC 关键字。
实例
从 "Websites" 表中选取所有网站，并按照 "alexa" 列排序：
SELECT * FROM Websites
ORDER BY alexa;

从 "Websites" 表中选取所有网站，并按照 "alexa" 列降序排序：
SELECT * FROM Websites
ORDER BY alexa DESC;

从 "Websites" 表中选取所有网站，并按照 "country" 和 "alexa" 列排序：
SELECT * FROM Websites 
ORDER BY country,alexa;
```

```
INSERT INTO :
语句用于向表中插入新记录。
语法
第一种：
INSERT INTO table_name
VALUES (value1,value2,value3,...);
第二种：
INSERT INTO table_name (column1,column2,column3,...)
VALUES (value1,value2,value3,...);

实例
向 "Websites" 表中插入一个新行：
INSERT INTO Websites (name,url,alexa,country)
VALUES('百度','https://www.baidu.com/','4','CN');

插入一个新行，但是只在 "name"、"url" 和 "country" 列插入数据（id 字段会自动更新）：
INSERT INTO Websites(name,url,country)
VALUES('stackoverflow','http://stackoverflow.com','IND');
```

```
UPDATE:
用于更新表中已存在的记录。

语法
UPDATE table_name
SET column1=value1,column2=value2,...
WHERE some_column=some_value;
**注意 SQL UPDATE 语句中的 WHERE 子句。WHERE 子句规定哪条记录或者哪些记录需要更新。如果您省略了 WHERE 子句，所有的记录都将被更新**

实例
把 "菜鸟教程" 的 alexa 排名更新为 5000，country 改为 USA：
UPDATE Websites
SET alexa = '5000',country = 'USA'
WHERE name = '菜鸟教程';

Update 警告！
在上面的实例中，如果我们省略了 WHERE 子句，如下所示：
UPDATE Websites
SET alexa='5000', country='USA'
执行以上代码会将 Websites 表中所有数据的 alexa 改为 5000，country 改为 USA。
执行没有 WHERE 子句的 UPDATE 要慎重，再慎重。

解决
在 MySQL 中可以通过设置 sql_safe_updates 这个自带的参数来解决，当该参数开启的情况下，你必须在update 语句后携带 where 条件，否则就会报错。
set sql_safe_updates=1; 表示开启该参数
```

```
DELETE:
用于删除表中的记录。

语法
DELETE FROM table_name
WHERE some_column=some_value;

请注意 SQL DELETE 语句中的 WHERE 子句！
WHERE 子句规定哪条记录或者哪些记录需要删除。如果您省略了 WHERE 子句，所有的记录都将被删除！

实例
从 "Websites" 表中删除网站名为 "百度" 且国家为 CN 的网站 ：
DELETE FROM Websites
WHERE name = '百度' AND country = 'CN';
 
关于删除的三个语句，DROP;TRUNCATE;DELETE的区别
DROP:
DROP test;
删除表test，并释放空间，将test删除的一干二净。

TRUNCATE:
TRUNCATE test;
删除表test里的内容，并释放空间，但不删除表的定义，表的结构还在。

DELETE:
1、删除指定数据
删除表test中年龄等于30的且国家为US的数据
DELETE FROM test WHERE age=30 AND country='US';
2、删除整个表
仅删除表test内的所有内容，保留表的定义，不释放空间。
DELETE FROM test 或者 DELETE FROM test;
DELETE * FROM test 或者 DELETE * FROM test;
```

# 高级使用方法
```
SELECT TOP:
用于规定要返回的记录的数目。

SQL Server / MS Access 语法:
SELECT TOP number|percent column_name(s)
FROM table_name;

实例
在 Microsoft SQL Server 中还可以使用百分比作为参数。
下面的 SQL 语句从 websites 表中选取前面百分之 50 的记录：
SELECT TOP 50 PERCENT * 
FROM Websites;

MySQL 语法:
SELECT column_name(s)
FROM table_name
LIMIT number;

实例
下面的 SQL 语句从 "Websites" 表中选取头两条记录：
SELECT  *   FROM  Websites
LIMIT 2;
```

```
LIKE 操作符
LIKE 操作符用于在 WHERE 子句中搜索列中的指定模式。

语法
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern;

实例
下面的 SQL 语句选取 name 以字母 "G" 开始的所有客户：
SELECT *
FROM Websites
WHERE name LIKE 'G%';

选取 name 包含模式 "oo" 的所有客户：
SELECT * FROM Websites
WHERE name LIKE '%oo%';

下面的 SQL 语句选取 name 不包含模式 "oo" 的所有客户：
SELECT * FROM Websites
WHERE name NOT LIKE '%oo%';
```

```
通配符
在 SQL 中,通配符与 SQL LIKE 操作符一起使用,用于搜索表中的数据。

grammar
[charlist]	字符列中的任何单一字符;
[^charlist]
或
[!charlist]	不在字符列中的任何单一字符

examples
下面的 SQL 语句选取 url 以字母 "https" 开始的所有网站：
SELECT * FROM Websites
WHERE url LIKE 'https%';

选取 name 以一个任意字符开始，然后是 "oogle" 的所有客户：
SELECT * FROM Websites
WHERE name LIKE '_oogle';

选取 name 以 "G" 开始，然后是一个任意字符，然后是 "o"，然后是一个任意字符，然后是 "le" 的所有网站：
SELECT * FROM Websites
WHERE LIKE 'G_o_le';

MySQL 中使用 REGEXP 或 NOT REGEXP 运算符 (或 RLIKE 和 NOT RLIKE) 来操作正则表达式。
下面的 SQL 语句选取 name 以 "G"、"F" 或 "s" 开始的所有网站：
SELECT * FROM Websites
WHERE name REGEXP '^[GFs]';

下面的 SQL 语句选取 name 以 A 到 H 字母开头的网站：
SELECT * FROM Websites
WHERE name REGEXP '^[A-H]';

选取 name 不以 A 到 H 字母开头的网站：
SELECT * FROM Websites
WHERE name REGEXP '^[^A-H]';
```

```
IN 操作符
IN 操作符允许您在 WHERE 子句中规定多个值。

语法
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1,value2,...);

实例
下面的 SQL 语句选取 name 为 "Google" 或 "菜鸟教程" 的所有网站：
SELECT * FROM Websites
WHERE name IN ('Google','菜鸟教程');
```

```
BETWEEN 操作符
选取介于两个值之间的数据范围内的值。这些值可以是数值、文本或者日期。

语法
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;

examples
下面的 SQL 语句选取 alexa 介于 1 和 20 之间的所有网站：
SELECT * FROM Websites
WHERE alexa BETWEEN 1 AND 20;

下面的 SQL 语句选取alexa介于 1 和 20 之间但 country 不为 USA 和 IND 的所有网站：
SELECT * FROM Websites
WHERE (alexa BETWEEN 1 AND 20) 
      AND 
      NOT country IN ('USA','IND');
      
下面的 SQL 语句选取 name 以介于 'A' 和 'H' 之间字母开始的所有网站：
SELECT * FROM Websites
WHERE name BERWEEN 'A' AND 'H';

下面的 SQL 语句选取 name 不介于 'A' 和 'H' 之间字母开始的所有网站：
SELECT * FROM Websites
WHERE name NOT BETWENN 'A' AND 'H';

示例表
下面是 "access_log" 网站访问记录表的数据，其中：
aid：为自增 id。
site_id：为对应 websites表的网站 id。
count：访问次数。
date：为访问日期。

mysql> SELECT * FROM access_log;
+-----+---------+-------+------------+
| aid | site_id | count | date       |
+-----+---------+-------+------------+
|   1 |       1 |    45 | 2016-05-10 |
|   2 |       3 |   100 | 2016-05-13 |
|   3 |       1 |   230 | 2016-05-14 |
|   4 |       2 |    10 | 2016-05-14 |
|   5 |       5 |   205 | 2016-05-14 |
|   6 |       4 |    13 | 2016-05-15 |
|   7 |       3 |   220 | 2016-05-15 |
|   8 |       5 |   545 | 2016-05-16 |
|   9 |       3 |   201 | 2016-05-17 |
+-----+---------+-------+------------+
选取 date 介于 '2016-05-10' 和 '2016-05-14' 之间的所有访问记录：
SELECT * FROM access_log
WHERE date BETWEEN '2016-05-10' AND '2016-05-14';

请注意，在不同的数据库中，BETWEEN 操作符会产生不同的结果！
在某些数据库中，BETWEEN 选取介于两个值之间但不包括两个测试值的字段。
在某些数据库中，BETWEEN 选取介于两个值之间且包括两个测试值的字段。
在某些数据库中，BETWEEN 选取介于两个值之间且包括第一个测试值但不包括最后一个测试值的字段。
因此，请检查您的数据库是如何处理 BETWEEN 操作符！
```



