# Build stage (uses Maven to create the JAR)
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
# Cache dependencies for faster rebuilds
RUN mvn dependency:go-offline -B
COPY src ./src
RUN mvn clean package -DskipTests

# Run stage (lightweight, only needs the JAR)
FROM openjdk:17-jdk-slim
WORKDIR /app
# Copy the built JAR from the builder stage
COPY --from=builder /app/target/quiz-service-*.jar /app/quiz-service.jar
# Expose the default Spring Boot port
EXPOSE 5002
# Optimized JVM flags for production
ENTRYPOINT ["java", "-Xmx512m", "-jar", "quiz-service.jar"]