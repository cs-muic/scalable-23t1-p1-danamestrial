## First stage, Build stage
FROM maven:3.8.6-jdk-11-slim AS builder

## Copy file to build
WORKDIR /project
COPY . /project

RUN mvn clean package

## Second stage, Package stage
FROM openjdk:11-jre-slim

COPY --from=builder /project/target/ums-1.0.jar ums.jar

ENTRYPOINT ["java","-jar","ums.jar"]