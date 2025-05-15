# --- Build stage ---
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline -B
COPY src ./src
RUN mvn clean package -DskipTests

# --- Run stage ---
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=builder /app/target/question-service-*.jar /app/question-service.jar

# Port must match `server.port` if defined (default is 8080 if not overridden)
EXPOSE 5000

ENTRYPOINT ["java", "-Xmx512m", "-jar", "question-service.jar"]
