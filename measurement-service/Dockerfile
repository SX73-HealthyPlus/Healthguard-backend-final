# Etapa 1: Construcción del JAR
FROM maven:3.8.7-eclipse-temurin-17 AS build

WORKDIR /app

COPY ./pom.xml ./pom.xml
COPY ./src ./src

RUN mvn clean package -DskipTests

# Etapa 2: Imagen final para producción
FROM eclipse-temurin:17-jdk

WORKDIR /app

COPY --from=build /app/target/*.jar measurement-service.jar

EXPOSE 8082

ENTRYPOINT ["java", "-jar", "measurement-service.jar"]
