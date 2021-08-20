
# Docker - connect 2 container using docker network 
# container 1 : mongodb
# container 2 : node.js app 

# Steps : 
create network : docker network create mynet
run mongo container : docker run -d --name mongodb --network mynet mongo
add the container name to mongo connect at app.js ( mongodb is the container name we want to connect ) :'mongodb://mongodb:27017/swfavorites',
build the image of the app : docker build -t app .
run the image as container via port 3000 :   docker run -d --rm --name favapp -p 3000:3000 --network mynet app



