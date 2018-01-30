# newwork
work submitted
Before using script you need to change environment variables for MYSQL connection, outlined below.
 
Example run command:
```sh
$ export MYSQL_ENV_HOST='localhost' 
$ export MYSQL_ENV_USER='sgolota'
$ export MYSQL_ENV_PASSWORD='**************'
$ export MYSQL_ENV_DATABASE='testdb'
```
## Mysql
In my example I use database `testdb`.
There are 3 tables in this database:
* apn
* ses
* version

Table `version` collects version of table:
```sh
mysql> select * from version; 
+--------+---------+
| tables | version |
+--------+---------+
| apn    |      10 |
| ses    |       0 |
+--------+---------+
```
I created mysqldump for database. You can use this file:
```sh
$ mysql  database < testdb.sql
```
## Testing
For testing I cleate 6 sql files in sql/:
```sh
001.ses.sql
001apn.sql
010.apn.sql
013apn.sql
014ses.sql
015.apn.sql
```
Each files insert 2 rows. For example file `001.ses.sql` insert 2 rows in table `ses` and insert version number (1) in first column:
```sh
INSERT INTO ses VALUES (001,'3g.utel.ua',10),(001,'3g.utel.ua',25);
```
File `015.apn.sql` insert 2 rows in table `apn`  and insert version number (15) in first column:
```sh
INSERT INTO apn VALUES (15,'3g.utel.ua',10),(15,'3g.utel.ua',25);
```

After executing  script upgradeDB.py we can see that 4 files were written to the database.
```sh
Find 4 new scripts:
013apn.sql
015.apn.sql
001.ses.sql
014ses.sql
 ```
 
