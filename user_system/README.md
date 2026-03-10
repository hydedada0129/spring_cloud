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


### project environment
#### create a Maven project (simple maven project)

#### change to spring boot
add relative dependencies of spring boot in pom.xml    
(spring boot parent, spring boot starter(web, test), spring boot maven plugin)  
create a main class  

### configuration yml
/src/main/resources/application.yml  
config: spring service's name, server's port  

### MyBatis: database access framework
#### add mybatis dependency 
pom.xml  

#### add mysql driver, connection pool(druid)
pom.xml   
<scope>runtime  
because spring boot loads JDBC driver as runtime  

#### add datasource configuration in application.yml
mysql, Druid config  

### Redis - for save Token
#### docker Redis, redis-cli
after installed, test it :  
set a 123  
get a

#### add redis dependency, service connects to redis configuration 
pom.xml  
application.yml

### implement business logic
#### controller, service, DAO  
##### controller: only receives request
##### service: handle request (executing logic)
service to service portocol (HTTP, Spring MVC): 

Controller(encapsulate the request into object and pass it to service layer):  
/user/getSmsCode  
/user/logiByMobile  
/user/loginExit  






## spring boot to spring cloud
### service registration center: Consul
in real world, create cluster deployment  
but here create a single Consul  

#### Docker for Consul

#### change to spring cloud
