FROM ubuntu:latest

ENV NODE_MAJOR=20

WORKDIR /app

RUN apt update && apt-get install -y curl && \
  curl -fsSl https://deb.nodesource.com/setup_${NODE_MAJOR}.x | bash - && \
  apt-get install -y nodejs && \
  echo "Node Version: " && node -v

COPY . .

RUN npm install

EXPOSE 8080

ENTRYPOINT [ "node", "server.js" ]