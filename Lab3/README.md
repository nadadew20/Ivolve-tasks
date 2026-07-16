# Dockerizing a Spring Boot Application

## Overview
This project demonstrates how to containerize a Java Spring Boot application using Docker.

## Prerequisites

- Docker
- Git

## Clone the Repository

```bash
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```

## Dockerfile

```dockerfile
FROM maven:3.9.6-eclipse-temurin-17

WORKDIR /app

COPY . .

RUN mvn clean package

EXPOSE 8080

CMD ["java","-jar","target/demo-0.0.1-SNAPSHOT.jar"]
```

## Build Docker Image

```bash
docker build -t app1 .
```

## Run the Container

```bash
docker run -d --name container1 -p 8080:8080 app1
```

## Test the Application

Open your browser and visit:

```
http://localhost:8080
```

Or use:

```bash
curl http://localhost:8080
```

## Stop and Remove the Container

```bash
docker stop container1
docker rm container1
```

## Docker Commands

List images:

```bash
docker images
```

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

## Author

Nada Hamdallah
