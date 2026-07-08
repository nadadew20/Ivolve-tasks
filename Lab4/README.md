# Lab 4 - Run Java Spring Boot App in a Docker Container

## Objective

Run a Java Spring Boot application inside a Docker container using a Java 17 base image.

---

## Prerequisites

- Docker
- Git
- Java 17
- Maven

---

## Clone the Repository

```bash
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```

---

## Build the Application

```bash
mvn clean package
```

After a successful build, the JAR file will be generated in:

```
target/demo-0.0.1-SNAPSHOT.jar
```

---

## Dockerfile

```dockerfile
FROM eclipse-temurin:17-jdk

WORKDIR /app

COPY target/demo-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
```

---

## Build the Docker Image

```bash
docker build -t app2 .
```

Check the image:

```bash
docker images
```

---

## Run the Container

```bash
docker run -d --name container2 -p 8080:8080 app2
```

Verify the container is running:

```bash
docker ps
```

---

## Test the Application

Open your browser and visit:

```
http://localhost:8080
```

Or test using:

```bash
curl http://localhost:8080
```

---

## Stop the Container

```bash
docker stop container2
```

---

## Remove the Container

```bash
docker rm container2
```

---

## Project Structure

```
Docker-1/
│── src/
│── target/
│── Dockerfile
│── pom.xml
└── README.md
```

---

## Technologies Used

- Java 17
- Spring Boot
- Maven
- Docker

---

## Author

**Nada Hamdallah**
