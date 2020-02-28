# spring-cloud-data-flow
Spring Cloud Data Flow Example with Kafka-binder 

###### Follow Below Steps

###### 1) Apache-Kafka Binary Distribution [Download](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.3.1/kafka_2.12-2.3.1.tgz).

###### 2) Strat Zookeeper server
> zookeeper-server-start.bat C:\Users\Documents\Office\kafka\config\zookeeper.properties

###### 3) Strat Kafka server 
> kafka-server-start.bat C:\Users\Documents\Office\kafka\config\server.properties

###### 4) Download Spring Cloud Skipper Server jar [Download] (https://repo.spring.io/snapshot/org/springframework/cloud/spring-cloud-skipper-server/2.4.0.BUILD-SNAPSHOT/spring-cloud-skipper-server-2.4.0.BUILD-20200216.134721-5.jar).

###### 5) Start Spring Cloud Skipper Server
> java -jar spring-cloud-skipper-server-2.4.0.BUILD-20200216.134721-5.jar

###### 6) Download Spring Cloud Data Flow Server jar [Download](https://repo.spring.io/snapshot/org/springframework/cloud/spring-cloud-dataflow-server/2.5.0.BUILD-SNAPSHOT/spring-cloud-dataflow-server-2.5.0.BUILD-20200228.034106-40.jar).

###### 7) Strat Spring Cloud Data Flow Server 
> java -jar spring-cloud-dataflow-server-2.5.0.BUILD-20200228.034106-40.jar

###### 8) Download Spring Cloud Data Flow Shell jar [Download](https://repo.spring.io/snapshot/org/springframework/cloud/spring-cloud-dataflow-shell/2.5.0.BUILD-SNAPSHOT/spring-cloud-dataflow-shell-2.5.0.BUILD-20200228.034106-40.jar).

###### 9) Strat Spring Cloud Data Flow shell 
> java -jar spring-cloud-dataflow-shell-2.5.0.BUILD-20200228.034106-40.jar

###### 10) Register all 3 microservices to Spring Cloud Data Flow Server using below commands
> app register --name product-service --type source --uri maven://com.javatechie:product-service:jar:0.0.1-SNAPSHOT

> app register --name discount-service --type processor --uri maven://com.javatechie:discount-service:jar:0.0.1-SNAPSHOT

> app register --name courier-service --type sink --uri maven://com.javatechie:courier-service:jar:0.0.1-SNAPSHOT

###### 11) Create Cloud Stream to connect between all microservices registered in spring cloud data flow server
> stream create --name log-data --definition 'product-service | discount-service | courier-service'

###### 10) Strat & Deploy Stream 
> stream deploy --name log-data
