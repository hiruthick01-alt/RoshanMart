
# Stage 1: Build RoshanMart using Java 17 and Maven
FROM maven:3.9-eclipse-temurin-17 AS build

WORKDIR /app

# Copy Maven configuration
COPY pom.xml .

# Copy application source code
COPY src ./src

# Build the executable Spring Boot JAR
RUN mvn clean package -DskipTests

# Stage 2: Run RoshanMart
FROM eclipse-temurin:17-jre

WORKDIR /app

# Copy the generated JAR from the build stage
COPY --from=build /app/target/roshan-mart-1.0.0.jar app.jar

# Railway supplies the PORT environment variable
EXPOSE 8080

# Start the application
ENTRYPOINT ["java", "-jar", "app.jar"]