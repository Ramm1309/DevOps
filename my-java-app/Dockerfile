# First stage: Build with Maven + JDK 17
FROM maven:3.8.7-openjdk-18 AS build

WORKDIR /app

COPY . .

# Build the project and skip tests
RUN mvn clean package -DskipTests

# Second stage: Use JRE 17 runtime
FROM openjdk:17-jdk-slim

WORKDIR /app

# Copy the built JAR from the first stage
COPY --from=build /app/target/my-java-app-1.0-SNAPSHOT.jar app.jar

# Expose the application port
EXPOSE 8081

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]

