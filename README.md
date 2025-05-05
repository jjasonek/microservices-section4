# Udemy Course Microservices with Spring Boot, Docker, Kubernetes Section4
https://www.udemy.com/course/master-microservices-with-spring-docker-kubernetes/
## spring version: 3.4.4
## Java 21


## Documentation
After adding the library, the swagger page is accessible through address 
http://localhost:8080/swagger-ui/index.html,
http://localhost:8090/swagger-ui/index.html,
http://localhost:9000/swagger-ui/index.html.


## Dockerization accounts by Docker file

### prepare JAR
cd accounts
mvn clean install
generated target\accounts-0.0.1-SNAPSHOT.jar

mvn spring-boot:run
application accounts is running on port 8080

java -jar .\target\accounts-0.0.1-SNAPSHOT.jar
application accounts is running on port 8080


### build the image
PS C:\Training\Microservices\section4\accounts> docker build . -t eazybytes/accounts:s4

PS C:\Training\Microservices\section4\accounts> docker images
REPOSITORY                  TAG       IMAGE ID       CREATED              SIZE
eazybytes/accounts          s4        a25eb3d0b593   About a minute ago   503MB
...

PS C:\Training\Microservices\section4\accounts> docker inspect a25


### run the container
PS C:\Training\Microservices\section4\accounts> docker run -d -p 8080:8080 eazybytes/accounts:s4
1c6d250644c21b96da477cf1d56b8fa0015543cd33c935625fac11bb5a740402

PS C:\Training\Microservices\section4\accounts> docker ps
CONTAINER ID   IMAGE                   COMMAND                  CREATED          STATUS          PORTS                               NAMES
1c6d250644c2   eazybytes/accounts:s4   "java -jar /accounts…"   43 seconds ago   Up 43 seconds   0.0.0.0:8080->8080/tcp              quirky_sutherland


## Dockerizing loans by Buildpacks

### build the image
PS C:\Training\Microservices\section4\accounts> cd ..\loans\
PS C:\Training\Microservices\section4\loans> mvn spring-boot:build-image
...
[INFO] Successfully built image 'docker.io/eazybytes/loans:s4'

PS C:\Training\Microservices\section4\loans> docker images
REPOSITORY                                 TAG       IMAGE ID       CREATED         SIZE
...
eazybytes/loans                            s4        5acf471ccc2d   45 years ago    310MB
paketobuildpacks/builder-jammy-java-tiny   latest    54ef03ee38f3   45 years ago    700MB

### note
size of the build image is 310MB in comparison with 503MB for accounts

### run the container
PS C:\Training\Microservices\section4\loans> docker run -d -p 8090:8090 eazybytes/loans:s4
beab93cb6b414c80df768d2a78f4a94b223df6abb4844a84bfcdb9805a7a7704
