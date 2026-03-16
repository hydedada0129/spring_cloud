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


VO(Value Object):  

前端透過 HTTP 傳送資料（例如 JSON 格式或表單參數）時，這些資料在本質上是分散的字串或數值。  

透過 VO，你可以將這些碎片化的資訊整合進一個結構化的 Java 物件中  


@Autowired annotation:  

我需要這個工具, Spring將會幫忙new物件的處理  

確保一個類別在整個應用程式運行期間，**只有一個實例（Instance）**存在。  


控制反轉 (IoC, Inversion of Control):  

原本由開發者主導的物件掌控權，轉交給了外部容器（如 Spring）  


##### DAO, MyBatis, yml

1.建立interface DAO

2.建立MyBatis Mapper XML(把 Java DAO method 對應到 SQL):  

在Eclipse下載外部DTD(Document Type Definition  

约束其核心配置文件和映射文件（Mapper XML）的结构、标签和属性，确保 XML 的有效性)

時會報錯, 即使設定：

勾選 Resolve external entities

改成 https

設定 Ignore

錯誤訊息依然存在, 但  

  1.MyBatis 會自己解析 XML  

  2.不需要 Eclipse 的 validator  

所以可以忽略.  


在Mapper XML中：  

#{}  → PreparedStatement（安全）  


3.Spring Boot 啟動時需要知道去哪裡把這兩者綁在一起:   application.yml加入mybatis XML路徑  


建立bootstrap.yml:  

bootstrap.yml要在spring cloud專案才能被讀取到. 因此要引入spring cloud的context依賴.  


== 比對的是「記憶體位址」，而 .equals() 比對的是「內容」  


UUID(Universally Unique Identifier): 唯一性較高  


access token 存入 Redis後, 要用key找到value  


## spring boot to spring cloud

### service registration center: Consul

in real world, create cluster deployment  

but here create a single Consul    


1.Spring Cloud Parent  

2.spring-actuator  

3.consul-discovery  

4.netflix-hystrix  

5.cloud commons  


1.bootstrap.yml  

   - spring.cloud.consul.discovery.instance-id  


1.pom.xml  

  - maven plugin

  - include: application, bootstrap yml files


1.Main Class: @EnableDiscoveryClient  


### Test:

Mock（模擬）物件:  

在單元測試中非常重要的技術  

隔離環境：當你想測試 UserController 的邏輯時，你不想真的連上 MySQL 或是扣掉簡訊點數，這時就可以用 Mock 的 UserSmsCodeDao 代替  


單元測試:  

使用 Spring Boot 內建的 JUnit 5 搭配 Mockito 框架  


#### Docker for Consul

docker pull consul:1.15  

docker run -d \

> --name consul \

> -p 8500:8500 \

> -v /tmp/consul/conf:/consul/conf \

> -v /tmp/consul/data:/consul/data \

> consul:1.15


Console:  

open browser: http://127.0.0.1:8500  


#### change to spring cloud

@EnableDiscoveryClient in Main Class  


#### run the spring cloud and check status from consul

launch spring cloud  

check consul console, user service is registered.  



