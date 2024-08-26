
# Desafio Icecast

Este repositório contém instruções para instalar e configurar o Icecast e o Nginx usando Docker. O Icecast é um serviço de streaming amplamente utilizado para transmissões de áudio e rádio, enquanto o Nginx pode ser usado para configurar um proxy reverso.

## 1. Instalação do Icecast via Docker

O Icecast é um serviço de streaming para transmissões de áudio e rádio, frequentemente utilizado em servidores GNU/Linux. Para iniciar o Icecast usando Docker, siga estas etapas:

1. **Executar o Container Icecast:**

   ```bash
   docker run --name icecast -p 8000:8000 --dns 8.8.8.8 --network bridge moul/icecast

Configurar o Icecast:

Após iniciar o container, acesse o diretório /etc/icecast2/icecast.xml dentro do container para verificar o user/password necessário para acessar o portal de administração do serviço de streaming.

Acesse  o Container

docker exec -it icecast /bin/bash


Navegue ate o diretorio 

cd /etc/icecast2/
cat icecast.xml

Com o serviço iniciado, você poderá transmitir áudio e voz. Confira o vídeo no Google Drive para verificar o funcionamento do Icecast e a transmissão de áudio e música.

2. Instalação do Nginx
A instalação do Docker Nginx pode ser feita usando o Docker Compose ou diretamente através das imagens disponíveis no Docker Hub. No exemplo abaixo, o servidor web Nginx é iniciado com o seguinte comando:

Executar o Container Nginx:

docker run --name nginx -p 80:80 --dns 8.8.8.8 --network bridge nginx
-p 80:80: Define a porta 80 para o servidor web Nginx.
--name nginx: Atribui o nome nginx ao container.
Configurar o Proxy Reverso:

Acesse o container Nginx com o comando:

docker exec -it nginx /bin/bash

Configure o proxy reverso para redirecionar as requisições para o servidor Icecast. Você pode fazer isso editando o arquivo de configuração do Nginx (/etc/nginx/nginx.conf ou criando um novo arquivo em /etc/nginx/conf.d/).

Exemplo de configuração de proxy reverso:

server {
    listen 80;

    location / {
        proxy_pass http://icecast:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

Atualmente, você pode realizar a subida dos containers de duas formas: usando o Docker Compose ou diretamente através das imagens disponíveis no Docker Hub. O próximo passo foi acessar o container através do comando docker exec -it nginx /bin/bash e criar o Proxy Reverso para redirecionar as requisições do Nginx ao servidor do Icecast.

3. Instâncias Docker
Docker é uma plataforma open source para virtualização de containers, oferecendo benefícios como isolamento e leveza em comparação com máquinas virtuais convencionais. Os containers são iniciados rapidamente e são ideais para desenvolvimento ágil e aplicações modernas, especialmente microserviços.

Imagem com os Containers em Execução
Os vídeos demonstrando os testes realizados do streaming Icecast podem ser visualizados através da URL: Vídeos de Testes do Icecast

O desafio foi realizado utilizando uma máquina GNU/Linux na Cloud AWS, e as portas necessárias foram liberadas para os serviços:

Porta 8000:
Porta 80 & 443 HTTP HTTPS
Porta 22 SSH para acesso a maquina remota onde foi realizado implementação do serviço de streaming


Imagens Docker

As imagens utilizadas encontra-se disponiveis para download no repositorio do Docker HUB, através dos links abaixo

#NGINX

https://hub.docker.com/layers/vitorsantosbh/nginx/latest/images/sha256-127262f8c4c716652d0e7863bba3b8c45bc9214a57d13786c854272102f7c945?context=repo

#ICECAST
https://hub.docker.com/repository/docker/vitorsantosbh/icecast/general
