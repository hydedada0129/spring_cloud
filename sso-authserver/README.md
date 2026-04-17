## OAuth 2.0 的4種角色：
#### Clinet (用戶端)：第三方Application端 (ex: Momo購物)，這裡的用戶端是指應用程式
#### Resource Owner : 使用者（ex: 微信使用者）
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
Clinet App Tables(認證中心:紀錄應用程式): client id（客戶端 ID）, client secret（客戶端密鑰）, resource ids（可以訪問哪些微服務）, scope（授權範圍）, authorized grant type（Client 支援哪種取得 Token 的方式）, web server redirect uri（使用授權碼模式（authorization_code）時，認證成功後要跳轉回來的網址）, authorities, access token validity, refresh token validity, additional info, autoapprove   
客戶端（Client）端存儲從認證伺服器（Auth Server）獲取到的 Token：  
記錄了目前系統中所有核發出去、且尚未過期的 Access Token:  
發放臨時 Code：認證成功後，伺服器會產生一個隨機字串（這就是 code），存入 oauth_code 表，然後把使用者重定向回你的 App，去找伺服器換真正的 access_token  
使用者（User）對應用程式（Client）的授權決定  


## 建構OAuth 2.0 授權認證微服務
### OAuth 2.0 標準授權認證協定
#### Dependency: Spring Cloud 提供 Starter整合dependency
oauth2, security

#### 設定授權認證微服務設定類別
##### 建立Spring設定類別
##### 加密證書
##### 設定Maven資源檔

#### Spring Security 安全設定類別
##### 建立Spring設定類別
