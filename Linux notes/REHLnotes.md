# Capstone 
* `VMRC` downloading requires VMware account, don't ask me why,   I don't want to sign up too...
* Tastatur: vorsichtig mit Buchstaben wie `z` und `y`
  * zur Login: en_us
  * GUI& CUI: de_de
`am besten diese Buchstaben in Passwort vermeiden`

#  MySQL 8.0
[Documentation from Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/deploying_different_types_of_servers/using-databases#introduction-to-mysql_assembly_using-mysql)

## Commands used
*for debug, backup, etc
install MySQL Server
on RHEL8
`yum module install mysql:8.0/server`
on Ubuntu 22.04
`sudo apt install mysql-server`
passwort rn: *will be changed in the end
`@UniKoeln123`

check MySQL version
`mysql -V`
check status
`sudo service mysql status`
check network status
`sudo ss -tap | grep mysql`
output looks like
`LISTEN     0      70                  127.0.0.1:33060         0.0.0.0:*     users:(("mysqld",pid=8058,fd=21))  `      
`LISTEN     0      151                 127.0.0.1:mysql         0.0.0.0:*     users:(("mysqld",pid=8058,fd=23))       `

if server runs incorrectly, you can restart it using
`sudo service mysql restart`

check systemd journal for troubleshooting
`sudo journalctl -u mysql`

error log in Ubuntu
`/var/log/mysql/error.log`
* Inside mysql command prompt `mysql>`
show all users in localhost
`show processlist;`
create a new database `test_db`;
`CREATE DATABASE test_db;`
show all datatbases
`SHOW DATABASES;`
select a certain db `test_db`
`USE test_db;`
show port
`SHOW GLOBAL VARIABLES LIKE 'PORT';`
create table in this db
```
create table tutorials_tbl(
   tutorial_id INT NOT NULL AUTO_INCREMENT,
   tutorial_title VARCHAR(100) NOT NULL,
   tutorial_author VARCHAR(40) NOT NULL,
   submission_date DATE,
   PRIMARY KEY ( tutorial_id )
);
```
INSERT INTO `tutorials_tbl` (`tutorial_id`,`tutorial_title`,`tutorial_author`,`submission_date`) VALUES ('13','sql_connect','mustermann','2022-11-16');
INSERT INTO `tutorials_tbl` (`tutorial_id`,`tutorial_title`,`tutorial_author`,`submission_date`) VALUES ('60','sql_connect2','mustermann2','2022-11-15');


>create table user_tbl(
    user_id VARCHAR(40) NOT NULL,
    user_pwd VARCHAR(100) NOT NULL,
    PRIMARY KEY ( user_id )
    );

>INSERT INTO user_tbl (user_id,user_pwd) VALUES ('admin1','123456');


list all tables in this db
`show tables;`
display contents in a table
`SELECT * FROM test_db.tutorials_tbl;`
## for remote connection 
==linux==
(no garantee for other OS)
* which would be disabled in the end, so that only webserver (on the same local machine as our database server) could access the DB
#### Config
to open the config file
`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`
* if you use nano as editor, then replace`vi` with `nano` .
* if this file is not in this directory, go to the topest directory (use `cd ..`) and try
`sudo find -name mysqld.cnf` to find the path
change `blind-address` to your IP-Address (or `0.0.0.0`, if you want it to be accessible to everyone)
*if you don't know your ip, 
`ip addr show`
`hostname -I`
`/sbin/ifconfig`



# test mysql Connetion on VM (localhost)
1. install mysql (done)
2. create test_db
3. create test_table, fill it with a few fake data
4. npm install mysql (in dir backend_test)
5. create server.js in this dir
6. fill it with mysql info (*notice: if host:"localhost" doesn't work, use 127.0.0.1



# MySQL Query
`SELECT * FROM tablename`:query all contents in this table
`SELECT * FROM tablename WHERE userName = ? and userPwd = ? `

* build it in Node:
connection.query('SELECT * FROM tablename WHERE userName = ? and userPwd = ? '), [variableName of 1st `?`, ... 2nd `?`],(err,results,fields)=>{

})