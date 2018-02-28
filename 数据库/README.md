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