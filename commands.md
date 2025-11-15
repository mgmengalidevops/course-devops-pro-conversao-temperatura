# Using Docker Commit

## Docker Commit

### Commands
``` bash
-docker container run -it -p 8080:8080  ubuntu /bin/bash
dentro do container
cat etc/os-release -> ver informações do SO
export DEBIAN_FRONTEND=noninteractive
apt update
apt install -y curl
curl -fsSL https://deb.nodesource.com/setup_23.x -o nodesource_setup.sh
bash nodesource_setup.sh
apt install -y nodejs
node -v
docker cp . 682d9d4deeee:/app
cd /app
npm i
node server.js
verificado dar um exit no container
docker commit 682d9d4deeee conversao-temperatura
docker container run -p 8080:8080 -it conversao-temperatura /bin/bash
docker container run -d -p 8080:8080 conversao-temperatura node /app/server.js
Entenendo melhor minha imgage
docker image ls
docker history conversao-temperatura
docker image inspect conversao-temperatura
```