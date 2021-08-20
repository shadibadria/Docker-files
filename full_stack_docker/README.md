
docker network create mynet

docker run --name mongodb -v data:/data/db --rm -d --network mynet   mongo

docker build -t frontend .

docker run --name frontend_server  --rm -p 3000:3000 -it  frontend

docker build -t backend .
docker run --name backend-server -d --rm --network mynet -p 80:80   backend

