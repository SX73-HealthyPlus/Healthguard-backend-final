# Etapa 1: Construcción del JAR
FROM maven:3.8.7-eclipse-temurin-17 AS build

WORKDIR /app

# Copiar los archivos de configuración de Maven
COPY ./pom.xml ./pom.xml
COPY ./src ./src

# Construir el archivo JAR
RUN mvn clean package -DskipTests

# Etapa 2: Imagen final para producción
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Copiar el archivo JAR construido desde la etapa anterior
COPY --from=build /app/target/*.jar api-gateway.jar

# Exponer el puerto que utiliza el api-gateway (generalmente 8080)
EXPOSE 8080

# Comando para ejecutar la aplicación
ENTRYPOINT ["java", "-jar", "api-gateway.jar"]
