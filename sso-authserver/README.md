## OAuth 2.0 的4種角色：
#### Clinet (用戶端)：第三方App端 (ex: Momo購物)，這裡的用戶端不是使用者
#### Resource Owner : 使用者
#### Resource Server : 受保護資源提供者 (ex: 微信， FB, Google)，儲存使用者資訊的伺服器
#### Authorizstion Server : 授權認證平台（有時候可以與Resource Server是同一個平台，如：微信開發平台）

## 建立Maven Simple專案 並改造成Spring Cloud
### pom改成Spring Cloud <parent>, 並引入其核心dependency:  
Consul discovery, 限流熔斷, 健康性檢查, 公共程式  
spring-boot-starter-web（把 Java 程序變成一个 Web 服務器）

### 基礎設定檔bootstrap.yml 
但Spring Boot不自動載入bootstrap, 需要pom另外引入
<plugin>,<resource>
### Entry Class
@SpringBootApplication    
@EnableDiscoveryClient  

## 啟動服務註冊中心Consul
### Docker 部屬
web console:http://127.0.0.1:8500   

### microservice 注入到 consul
啟動微服務  
看到console訊息：Registering service with consul表示註冊consul成功  
開啟browser http://127.0.0.1:8500
##### 完成以上步驟，就完成微服務架設

## MySQL設定
### Druid, JDBC driver, starter jdbc
### 設定連接：application.yml

## Docker 建立MySQL資料庫
### 建立資料庫： auth
### 資料表建立： 使用者資源，授權認證
#### 使用者資源資料庫
#### Client設定資訊表（App用戶端），Client授權資訊表（App用戶端Token），預授權碼資料表，授權Token資訊表（正式access token資訊）
