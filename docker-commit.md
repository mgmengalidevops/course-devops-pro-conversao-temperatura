
# Criando uma Imagem Docker usando Docker Commit

## 1. Iniciando um container Ubuntu
```bash
docker container run -it -p 8080:8080 ubuntu /bin/bash
```

## 2. Configurando o ambiente dentro do container
```bash
# Verificar informações do SO
cat etc/os-release

# Configurar frontend não interativo
export DEBIAN_FRONTEND=noninteractive


# Atualizar pacotes
apt update

# Instalar curl
apt install -y curl

# Baixar e instalar Node.js
curl -fsSL https://deb.nodesource.com/setup_23.x -o nodesource_setup.sh
bash nodesource_setup.sh
apt install -y nodejs

# Verificar versão do Node.js
node -v
```

## 3. Copiando arquivos para o container
```bash
# Copiar arquivos do host para o container (executar em outro terminal)
docker cp . 682d9d4deeee:/app
```

## 4. Configurando a aplicação dentro do container
```bash
cd /app
npm i
node server.js
```

## 5. Criando a imagem usando docker commit
```bash
# Sair do container
exit

# Criar imagem usando docker commit
docker commit 682d9d4deeee conversao-temperatura
```

## 6. Testando a nova imagem
```bash
# Executar container em modo interativo
docker container run -p 8080:8080 -it conversao-temperatura /bin/bash

# Executar aplicação em background
docker container run -d -p 8080:8080 conversao-temperatura node /app/server.js
```

## 7. Inspecionando a imagem criada
```bash
# Listar imagens
docker image ls

# Ver histórico da imagem
docker history conversao-temperatura

# Inspecionar detalhes da imagem
docker image inspect conversao-temperatura
```

