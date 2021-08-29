
# Docker compose 
---------------------
 Docker Compose 
---------------------
docker-compose up -d server php mysql
docker-compose run --rm  composer create-project --prefer-dist laravel/laravel .
sudo chmod -R o+w src/storage src/bootstrap/cache