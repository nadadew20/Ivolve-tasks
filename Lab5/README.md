# Lab 5 - Multi-Stage Docker Build

## Objective

Create a multi-stage Docker image for a Java Maven application.

## Steps

1. Clone the repository.
2. Create a multi-stage Dockerfile.
3. Build the application using Maven.
4. Copy the generated JAR into a lightweight Java runtime image.
5. Expose port 8080.
6. Run the application.

## Build Image

```bash
docker build -t app3 .
```

## Run Container

```bash
docker run -d --name container3 -p 8080:8080 app3
```

## Test

Open:

```
http://localhost:8080
```

or

```bash
curl http://localhost:8080
```

## Stop and Remove

```bash
docker stop container3
docker rm container3
```

## Remove Image

```bash
docker rmi app3
```

## Dockerfile

```dockerfile
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
```
