FROM maven:3.8.4-jdk-11-slim AS builder

COPY . app/worker/

WORKDIR /app/worker/

RUN mvn dependency:resolve
RUN mvn package


FROM openjdk:11-jre-slim

COPY --from=builder  /app/worker/target/worker-jar-with-dependencies.jar /app/worker/

WORKDIR /app/worker/

CMD java -jar worker-jar-with-dependencies.jar
