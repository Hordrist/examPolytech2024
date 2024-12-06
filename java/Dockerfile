FROM maven:3-eclipse-temurin-8-alpine AS maven
WORKDIR /usr/src/app
COPY . .
RUN mvn clean package -DskipTests

FROM eclipse-temurin:8-jre-alpine
EXPOSE 8448
WORKDIR /usr/src/app
COPY --from=maven /usr/src/app/target/java-*.jar /usr/src/app/app.jar
CMD ["java","-jar","app.jar"]