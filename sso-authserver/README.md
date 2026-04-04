## 建立Maven Simple專案 並改造成Spring Cloud
### pom改成Spring Cloud <parent>, 並引入其核心dependency:  
Consul discovery, 限流熔斷, 健康性檢查, 公共程式  
### 基礎設定檔bootstrap.yml 
但Spring Boot不自動載入bootstrap, 需要pom另外引入
<plugin>,<resource>
### Entry Class
@SpringBootApplication    
@EnableDiscoveryClient  

## 

