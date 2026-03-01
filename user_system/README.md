# user_system service

### system design: business logic, database
#### log in logic: 
one is mobile number + sms
one is 3rd party account

### create a docker mysql, createt 2 tables, one is user_info, one is sms_code_verify
* docker mysql image name : dev-mysql
* launch by ubuntu terminal: `docker start dev-mysql`
* list the docker container: `docker ps`
* check the mysql's port 3306: `sudo lsof -i :3306`
* create a table: `docker exec -it dev-mysql mysql -u root -p`
* enter mysql sql command for creating a table: `create database userdb;`
* list out the schemas: `show databases;`
* after created, use the table: `use userdb;`
* sql command for creating table: `create table user_info(....);`
* list out the table: `show tables;`
* show the columns: `describe user_info;`

### 
