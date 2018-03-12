- 安装

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
