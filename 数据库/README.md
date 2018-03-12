1、查看数据表中字符集设置

> mysql> SHOW CREATE TABLE tablename

2、修改 MYSQL 表的字符集


>mysql> ALTER TABLE tbl_name CONVERT TO CHARACTER SET charset_name;

3、导出数据库(想要包含数据就把-d去掉）

>mysqldump -u root -p -d dbname > db.sql;

4、导出数据库表(想要包含数据就把-d去掉）

>mysqldump -u root -p -d dbname tablename > db.sql;

5、导入数据库(导入表要先选择好数据库）

>source db.sql;

- mysql安装

```
my.ini

[client]
default-character-set=utf8
[mysql]
default-character-set=utf8
[mysqld]
default-character-set=utf8

#basedir代表自己MySQL的安装根目录
basedir = C:\\mysql-5.7.21-winx64

#datadir代表自己MySQL的数据库保存的目录，如果没有在MySQL安装的根目录下新建一个data文件夹 
datadir = C:\\mysql-5.7.21-winx64\\data

#port代表端口号
#port = 3306
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES 
```
