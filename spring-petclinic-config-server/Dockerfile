# Multi-stage Dockerfile for Spring Petclinic Config Server

# Stage 1: Build the application
FROM maven:3.8.4 AS builder
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Create a minimal runtime image
FROM adoptopenjdk/openjdk11:alpine-jre
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar
CMD ["java", "-jar", "app.jar"]
