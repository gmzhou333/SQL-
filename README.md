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
SELECT * FROM Websites
WHERE country = 'CN';
and
SELECT * FROM Websites
WHERE id = 1;

逻辑运算的优先级：
() not and or

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
SELECT  studentNO  FROM student WHERE 1
或者
SELECT studentNO FROM student WHERE 'abc'
都将返回student表所有行记录的studentNO列。因为每一行记录WHERE都返回true。
```







