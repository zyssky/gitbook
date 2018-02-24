1、查看数据表中字符集设置

> mysql> SHOW CREATE TABLE tablename

2、修改 MYSQL 表的字符集


>mysql> ALTER TABLE tbl_name CONVERT TO CHARACTER SET charset_name;