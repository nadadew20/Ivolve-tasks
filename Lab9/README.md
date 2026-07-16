# Lab 9 - Containerized Node.js and MySQL Stack Using Docker Compose

## Description
This project runs a Node.js application with a MySQL database using Docker Compose.

## Technologies
- Docker
- Docker Compose
- Node.js
- MySQL 8

## Prerequisites
- Docker
- Docker Compose

## Run the project

```bash
docker compose up --build -d
```

## Verify

Application:
```
http://localhost:3000
```

Health endpoint:
```
http://localhost:3000/health
```

Ready endpoint:
```
http://localhost:3000/ready
```

## Stop

```bash
docker compose down
```
