# Etapa 1: build con Maven
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Etapa 2: runtime con JDK
FROM eclipse-temurin:17-jdk
WORKDIR /app

# Copiar el JAR compilado
COPY --from=build /app/target/*.jar app.jar

# Copiar el application.properties local
COPY src/main/resources/application.properties /app/application.properties

EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
