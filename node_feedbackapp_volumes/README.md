
# Docker bind mount 

# OPTION 1 WITHOUT USING DOCKER  VOLUMES in docker file:  
docker run -d -p 3000:80 --rm  --name aapp -v feedback:/app/feedback -v "PATH_TO_PROJECT_DIR:/app" -v /app/node_modules  myimage

# OPTION 2 USING DOCKER VOLUMES in docker file : 
docker run -d -p 3000:80 --rm  --name aapp -v feedback:/app/feedback -v "PATH_TO_PROJECT_DIR:/app"  myimage

