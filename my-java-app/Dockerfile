# Use Maven to build the application
FROM maven:3.8.7-openjdk-11-slim AS build

WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Create the final image
FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=build /app/target/my-java-app-1.0-SNAPSHOT.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
