## Install

> $ sudo yum install MariaDB-server MariaDB-client  
$ service mysql start  
[Mariadb Repository](https://mariadb.com/kb/en/mariadb/yum/)  


## Mysql 자주 사용하는 명령어  
  
### SHOW VARIABLES; 
> 시스템 변수 값 보기 [>설명보기](https://dev.mysql.com/doc/refman/8.0/en/show-variables.html)    
$ SHOW VARIABLES LIKE 'expire_logs_days';  
$ SHOW GLOBAL VARIABLES LIKE '%size%';  
$ SET GLOBAL expire_logs_days = 5;    // 로그기록 5일로 설정하기 


```show
SHOW Syntax
https://dev.mysql.com/doc/refman/8.0/en/show.html

13.7.6.1 SHOW BINARY LOGS Syntax
13.7.6.2 SHOW BINLOG EVENTS Syntax
13.7.6.3 SHOW CHARACTER SET Syntax
13.7.6.4 SHOW COLLATION Syntax
13.7.6.5 SHOW COLUMNS Syntax
13.7.6.6 SHOW CREATE DATABASE Syntax
13.7.6.7 SHOW CREATE EVENT Syntax
13.7.6.8 SHOW CREATE FUNCTION Syntax
13.7.6.9 SHOW CREATE PROCEDURE Syntax
13.7.6.10 SHOW CREATE TABLE Syntax
13.7.6.11 SHOW CREATE TRIGGER Syntax
13.7.6.12 SHOW CREATE USER Syntax
13.7.6.13 SHOW CREATE VIEW Syntax
13.7.6.14 SHOW DATABASES Syntax
13.7.6.15 SHOW ENGINE Syntax
13.7.6.16 SHOW ENGINES Syntax
13.7.6.17 SHOW ERRORS Syntax
13.7.6.18 SHOW EVENTS Syntax
13.7.6.19 SHOW FUNCTION CODE Syntax
13.7.6.20 SHOW FUNCTION STATUS Syntax
13.7.6.21 SHOW GRANTS Syntax
13.7.6.22 SHOW INDEX Syntax
13.7.6.23 SHOW MASTER STATUS Syntax
13.7.6.24 SHOW OPEN TABLES Syntax
13.7.6.25 SHOW PLUGINS Syntax
13.7.6.26 SHOW PRIVILEGES Syntax
13.7.6.27 SHOW PROCEDURE CODE Syntax
13.7.6.28 SHOW PROCEDURE STATUS Syntax
13.7.6.29 SHOW PROCESSLIST Syntax
13.7.6.30 SHOW PROFILE Syntax
13.7.6.31 SHOW PROFILES Syntax
13.7.6.32 SHOW RELAYLOG EVENTS Syntax
13.7.6.33 SHOW SLAVE HOSTS Syntax
13.7.6.34 SHOW SLAVE STATUS Syntax
13.7.6.35 SHOW STATUS Syntax
13.7.6.36 SHOW TABLE STATUS Syntax
13.7.6.37 SHOW TABLES Syntax
13.7.6.38 SHOW TRIGGERS Syntax
13.7.6.39 SHOW VARIABLES Syntax
13.7.6.40 SHOW WARNINGS Syntax
```

### Mysqld_safe  
> mysql start  
$ service mysql start  
or  
$ mysqld_safe --user=mysql --skip-name-resolve &  

### Mysqladmin  
> $ mysqladmin -uroot -p shutdown  
$ mysqladmin -uroot -p processlist -i3  
__특정 User의 processlist all kill__  
$ kill USER username;

### Mysqlcheck
> 전체 체크 및 자동 복구  [설명보기](https://dev.mysql.com/doc/refman/8.0/en/mysqlcheck.html)
$ mysqlcheck -Aa --auto-repair -uroot -p  
$ mysqlcheck -Ao --auto-repair -uroot -p  
```code
-A   --all-database
-a   --analyze
-o   --optimize
-P   --port
```
> 특정 데이터베이스 or 테이블만 체크 및 복구  
$ mysqlcheck -uroot -p --auto-repair [[database]]  
$ mysqlcheck -uroot -p --auto-repair [[database]] [[tablename]]   
특정 DB의 모든 테이블 최적화  
$ mysqlcheck -uroot -p --optimize [[DB명]]  
mysql> check table [[tablename]]   //체크  
mysql> repair table [[tablename]]   // 복구  
mysql> optimize table [[tablename]]  //최적화    
mysql> analyze table [[tablename]]  
  
###   
