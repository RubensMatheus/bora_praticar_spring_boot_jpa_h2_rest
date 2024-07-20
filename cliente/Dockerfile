# Use a imagem oficial do Maven para a fase de build
FROM maven:3.8.4-openjdk-17 AS build
COPY src app/src
COPY pom.xml /app
WORKDIR /app
#COPY . .
RUN mvn clean install

# Use uma imagem JDK leve para a fase de runtime
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
