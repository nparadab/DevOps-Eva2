# Etapa 1: build con Maven
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Etapa 2: runtime con JDK
FROM eclipse-temurin:17-jdk
WORKDIR /app

# Copiar el JAR compilado (igual que antes)
COPY --from=build /app/target/*.jar app.jar

# Copiar el application.properties de Ventas
COPY back-Ventas_SpringBoot/Springboot-API-REST/src/main/resources/application.properties /app/application.properties

EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
