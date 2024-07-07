# Use Maven for build stage with the specified JDK version
FROM maven:3.8.5-openjdk-15 AS build

# Copy the entire project into the build stage
COPY . .

# Build the project and skip tests
RUN mvn clean package -DskipTests

# Use a slim OpenJDK image for the final stage
FROM openjdk:15-jdk-slim

# Copy the built JAR file from the build stage
COPY --from=build /target/Nutro-ass-0.0.1-SNAPSHOT.jar Nutro-ass.jar

# Expose port 8080
EXPOSE 8082

# Set the entry point to run the JAR file
ENTRYPOINT ["java", "-jar", "Nutro-ass.jar"]
