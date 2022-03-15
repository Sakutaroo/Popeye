FROM maven:3.5-jdk-8-alpine AS builder

COPY . app/worker/

WORKDIR /app/worker/

RUN mvn dependency:resolve
RUN mvn package


FROM openjdk:8-jre-alpine

COPY --from=builder  /app/worker/target/worker-jar-with-dependencies.jar /app/worker/

WORKDIR /app/worker/

CMD java -jar worker-jar-with-dependencies.jar
