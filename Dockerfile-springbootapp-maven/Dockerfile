#Setting up build container for maven.
FROM maven:3.8.6-openjdk-18 AS build 
#This line copies the source code of java spring application into docker container.
COPY src /home/app/src
#This line copies pom.xml (configuartion file of maven project) into docker container.
COPY pom.xml /home/app
#This command builds the source code and creates .jar file that will store the application.
RUN mvn -f /home/app/pom.xml clean package

#Setting up java runtime docker container.
FROM openjdk:8-jdk-alpine
#This line copies the .jar file that we generated previosly by running maven build command. This .jar file has the entire java application inside of it.
COPY --from=build /home/app/target/spring-boot-app-1.0-SNAPSHOT.jar /usr/local/lib/spring-boot-app.jar
#This line just exposes 8080 port.  
EXPOSE 8080
#This command starts java applicatin.
ENTRYPOINT ["java","-jar","/usr/local/lib/spring-boot-app.jar"]


#The first container (build container) is deleted after the first initial build because we dont need it anymore. We have .jar file that we already generated.
