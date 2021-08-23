
# Docker compose 
---------------------
 Docker Compose 
---------------------
docker-compose up -d  - start \
docker-compose down -v - stop

# or use manual steps :

---------------------
Create Network
---------------------

docker network create mynet

---------------------
Run MongoDB Container
---------------------

docker run --name mongodb \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=secret \
  -v data:/data/db \
  --rm \
  -d \
  --network mynet \
  mongo

---------------------
Build Node API Image
---------------------

docker build -t backend_image .

---------------------
Run Node API Container
---------------------

docker run --name backend_server \
  -e MONGODB_USERNAME=admin \
  -e MONGODB_PASSWORD=secret \
  -v logs:/app/logs \
  -v /root/Docker-files/full_stack_docker/backend:/app \
  -v /app/node_modules \
  --rm \
  -d \
  --network mynet \
  -p 80:80 \
  backend_image

---------------------
Build React  Image
---------------------

docker build -t frontend_image .

---------------------
Run React  Container
---------------------

docker run --name frontend_server \
  -v /root/Docker-files/full_stack_docker/frontend/src:/app/src \
  --rm \
  -d \
  -p 3000:3000 \
  -it \
frontend_image
---------------------
Stop all Containers
---------------------

docker stop mongodb backend_server frontend_server

