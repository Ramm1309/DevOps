# First stage: Build the application using Maven
FROM maven:3.8.7-openjdk-18 AS build

WORKDIR /app

COPY . .

# Build the project and skip tests
RUN mvn clean package -DskipTests

# Second stage: Use OpenJDK 11 runtime
FROM openjdk:11-jre-slim

WORKDIR /app

# Copy the built JAR from the first stage
COPY --from=build /app/target/my-java-app-1.0-SNAPSHOT.jar app.jar

# Expose the application port (8081 as per your requirement)
EXPOSE 8081

# If your app is a web service (Spring Boot, etc.), this will keep it running:
ENTRYPOINT ["java", "-jar", "app.jar"]

# If your app is a batch job and you need to keep the container running (useful for debugging):
# Uncomment this line below if it's a batch job
# CMD ["sh", "-c", "java -jar app.jar && tail -f /dev/null"]
