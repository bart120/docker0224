FROM maven:3.9.6-eclipse-temurin-17-alpine as build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests
FROM openjdk:17-jdk-slim as final
WORKDIR /app
ARG JAR_VERSION=2.0
COPY --from=build /app/target/demo-${JAR_VERSION}.jar ./demo.jar
ENTRYPOINT [ "java", "-jar", "demo.jar"]

#docker build -t rest-spring:v1-beta --build-arg JAR_VERSION=1.0 .