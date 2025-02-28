FROM maven:3.6.3-openjdk-8-slim AS builder

WORKDIR /app

COPY pom.xml .

RUN mvn dependency:go-offline -B

COPY src/ ./src/

RUN mvn clean package -DskipTests -B

FROM openjdk:8-jre-slim

WORKDIR /app

COPY --from=builder /app/target/users-api-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8083

CMD ["java", "-jar", "app.jar"]
