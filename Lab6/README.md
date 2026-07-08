# Lab 6 - Managing Docker Environment Variables

## Objective

Learn how to manage Docker environment variables using three different methods.

## Steps

### Clone Repository

```bash
git clone https://github.com/Ibrahim-Adel15/Docker-3.git
cd Docker-3
```

### Build Image

```bash
docker build -t docker-lab6 .
```

### Method 1 - Command Line Variables

```bash
docker run -d \
--name app-dev \
-p 8081:8080 \
-e APP_MODE=development \
-e APP_REGION=us-east \
docker-lab6
```

### Method 2 - Environment File

Create `staging.env`

```text
APP_MODE=staging
APP_REGION=us-west
```

Run:

```bash
docker run -d \
--name app-stage \
-p 8082:8080 \
--env-file staging.env \
docker-lab6
```

### Method 3 - Dockerfile ENV

The Dockerfile contains:

```dockerfile
ENV APP_MODE=production
ENV APP_REGION=canada-west
```

Run:

```bash
docker run -d \
--name app-prod \
-p 8083:8080 \
docker-lab6
```

## Verify

```bash
docker ps
docker exec app-dev env
docker exec app-stage env
docker exec app-prod env
```
