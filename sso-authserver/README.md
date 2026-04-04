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
