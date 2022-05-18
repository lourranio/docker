
# GITLAB UTILIZANDO DOCKER

## Descrição

Aqui é utilizado o docker para subir a aplicação do gitlab.
No script do docker, é utilizado "Volume Docker". Entao, é necessario criar antes.
Caso nao deseje criar o volume, basta remover a linha.

Exemplo: 
  1. Antes - com Volume Docker
     docker run --detach \
  --publish 1443:443 --publish 8080:80 --publish 1001:22 \
  --name gitlab \
  --restart always \
  --volume gitlab_config:/etc/gitlab \
  --volume gitlab_logs:/var/log/gitlab \
  --volume gitlab_data:/var/opt/gitlab \
  --shm-size 2gb \
  gitlab/gitlab-ce:latest
  
  2. Depois - Sem Volume
     docker run --detach \
  --publish 1443:443 --publish 8080:80 --publish 1001:22 \
  --name gitlab \
  --restart always \
  --shm-size 2gb \
  gitlab/gitlab-ce:latest
    
