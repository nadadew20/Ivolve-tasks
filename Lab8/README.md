# Lab 8 - Custom Docker Network for Microservices

## Objective
This lab demonstrates how to create Docker images for frontend and backend microservices and connect them using a custom Docker network.

## Project Structure

```
Lab8/
├── frontend/
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
│
├── backend/
│   ├── Dockerfile
│   └── app.py
│
└── README.md
```

## Frontend Dockerfile
- Uses the Python base image.
- Installs dependencies from `requirements.txt`.
- Exposes port **5000**.
- Runs the application using:
  ```bash
  python app.py
  ```

## Backend Dockerfile
- Uses the Python base image.
- Installs Flask.
- Exposes port **5000**.
- Runs the application using:
  ```bash
  python app.py
  ```

## Steps Performed

1. Cloned the project repository.
2. Created Docker images for the frontend and backend.
3. Created a custom Docker network named **ivolve-network**.
4. Ran the backend container on the custom network.
5. Ran **frontend1** on the custom network.
6. Ran **frontend2** on the default bridge network.
7. Verified that:
   - **frontend1** could communicate with the backend.
   - **frontend2** could not communicate with the backend because it was on a different network.

## Docker Commands

### Build Images

```bash
docker build -t frontend-image ./frontend
docker build -t backend-image ./backend
```

### Create Network

```bash
docker network create ivolve-network
```

### Run Containers

```bash
docker run -d --name backend --network ivolve-network -p 5001:5000 backend-image

docker run -d --name frontend1 --network ivolve-network -p 5002:5000 frontend-image

docker run -d --name frontend2 -p 5003:5000 frontend-image
```

### Verify Network

```bash
docker network inspect ivolve-network
```

### Remove Containers

```bash
docker rm -f backend frontend1 frontend2
```

### Remove Network

```bash
docker network rm ivolve-network
```

## Technologies Used

- Docker
- Docker Networking
- Python
- Linux
