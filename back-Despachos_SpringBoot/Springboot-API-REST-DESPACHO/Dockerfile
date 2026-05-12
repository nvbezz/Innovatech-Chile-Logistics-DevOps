FROM maven:3.9-eclipse-temurin-17 AS builder
WORKDIR /build
COPY pom.xml .
RUN mvn dependency:go-offline
COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jre-alpine AS runtime
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
WORKDIR /app
COPY --from=builder /build/target/Springboot-API-REST-DESPACHO-0.0.1-SNAPSHOT.jar app.jar
RUN chown appuser:appgroup app.jar
USER appuser
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "app.jar"]
