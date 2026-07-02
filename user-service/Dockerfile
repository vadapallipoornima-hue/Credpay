FROM maven:3.9-eclipse-temurin-21 AS build 
WORKDIR /build
COPY pom.xml .
RUN mvn dependency:go-offline  //download dependencies
COPY src ./src
RUN mvn clean package -DskipTests     //builds the application and creates a jar file in the target directory
RUN ls -l /build/target

FROM eclipse-temurin:21-jre-alpine 
WORKDIR /app
COPY --from=build /build/target/*.jar app.jar
USER appuser              // optional: run as non-root user for security
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]



