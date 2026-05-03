FROM maven:3.9-eclipse-temurin-17 AS build

COPY . /app

WORKDIR /app

RUN mvn clean package -DskipTests

RUN ls -la /app/target


FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

COPY --from=build /app/target/*.jar /app/app.jar

EXPOSE 8080

CMD ["java", "-jar", "/app/app.jar"]