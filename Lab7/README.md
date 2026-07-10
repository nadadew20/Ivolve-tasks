# Lab 7: Docker Volume and Bind Mount with Nginx

## Objective

Learn how to use Docker Volumes and Bind Mounts with an Nginx container.

## Steps

1. Create a Docker volume named `nginx_logs`.
2. Create a local directory `nginx-bind/html`.
3. Create an `index.html` file with:
   Hello from Bind Mount

4. Run an Nginx container with:
- Volume mounted to `/var/log/nginx`
- Bind mount to `/usr/share/nginx/html`
5. Verify the page using:

curl http://localhost:8080

6. Modify the HTML file and verify the changes immediately.
7. Verify Nginx logs are stored inside the Docker volume.

## Commands Used

```bash
docker volume create nginx_logs

mkdir -p ~/nginx-bind/html

echo "Hello from Bind Mount" > ~/nginx-bind/html/index.html

docker run -d \
--name nginx-lab \
-p 8080:80 \
-v nginx_logs:/var/log/nginx \
-v ~/nginx-bind/html:/usr/share/nginx/html \
nginx

curl http://localhost:8080

docker volume inspect nginx_logs

docker stop nginx-lab
docker rm nginx-lab

docker volume rm nginx_logs
Expected Output
Nginx serves the custom HTML page.
Changes to index.html appear instantly.
Logs are stored in the Docker volume.
