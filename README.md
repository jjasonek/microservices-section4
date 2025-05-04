# Udemy Course Microservices with Spring Boot, Docker, Kubernetes Section4
https://www.udemy.com/course/master-microservices-with-spring-docker-kubernetes/
## spring version: 3.4.4
## Java 21


## Documentation
After adding the library, the swagger page is accessible through address 
http://localhost:8080/swagger-ui/index.html,
http://localhost:8090/swagger-ui/index.html,
http://localhost:9000/swagger-ui/index.html.


## Dockerization by Docker file

cd accounts
mvn clean install
generated target\accounts-0.0.1-SNAPSHOT.jar

mvn spring-boot:run
application accounts is running on port 8080

java -jar .\target\accounts-0.0.1-SNAPSHOT.jar
application accounts is running on port 8080
