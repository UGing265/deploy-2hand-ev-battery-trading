# abc

# Source project 
https://github.com/lgdlong/g3-swp391-2hand-ev-battery-trading 

note: 
- You can put Dockerfile to api or web corresponding to structure project. Then build it if you want create new repository on dockerhub
- You can run directly docker-compose.yml with command **"docker compose up -d"**
- This project need **.env** that you need to contact me to get it


## Commands
- docker compose up -d   start
- docker compose down    down
- docker compose pull    pull from dockerhub
- docker ps              check active images
- docker images          check active images 

check logs
- docker logs evbattery-web -f
- docker logs evbattery-api -f
