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
- mysql> use RUNOOB;
- mysql> set names utf8;
- mysql> SELECT * FROM Websites;
'''

+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+
5 rows in set (0.01 sec)
'''


- use RUNOOB：选择数据库
- set names utf8：用于设置使用的字符集，字符集中可以出现中文
- SELECT * FROM Websites： 读取数据表的信息
- 上面的表包含五条记录（每一条对应一个网站信息）和5个列（id、name、url、alexa 和country）






