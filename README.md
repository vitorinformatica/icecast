# icecast
desafio icecast

1 - Instalação do Serviço via Docker
Icecast é um serviço de streaming amplamente utilizado para transmissões de áudio e rádio, especialmente em empresas que transmitem conteúdo. Ele é instalado em servidores GNU/Linux.
Para iniciar o Icecast usando Docker, execute o seguinte comando:
docker run --name icecast -p 8000:8000 --dns 8.8.8.8 --network bridge  moul/icecast
-p = parâmetro que define a porta que sera utilizado a aplicação
--name = nome que vai ser atribuído ao container 

Após iniciar o container, acesse o diretório /etc/icecast2/icecast.xml para verificar o user/password necessário para acessar o portal de administração do serviço de streaming. Com o serviço iniciado, você poderá transmitir áudio e voz. Conforme demonstrado no vídeo no Google Drive, o Icecast foi iniciado e transmitiu áudio e música.

Acessar o container, ir no diretório “/etc/icecast2/icecast.xml” e verificar user/password para acessar o portal de administração do serviço de streaming.
Ao clicar em iniciar o mesmo conecta ao servidor onde e possível transmitir através de áudio e voz, conforme vídeo no “Google Driver” o mesmo foi iniciado e transmitido áudio e música reproduzida.


2 - Instalação do Nginx
A instalação do Docker Nginx pode ser feita usando o Docker Compose ou diretamente através das imagens disponíveis no Docker Hub.
Neste exemplo, o servidor web Nginx foi iniciado com o seguinte comando:
docker run --name nginx -p 80:80 --dns 8.8.8.8 --network bridge nginx
Em seguida, acesse o container Nginx com o comando:
docker exec -it nginx /bin/bash
Foi configurado um Proxy Reverso para redirecionar as requisições para o servidor Icecast.
Atualmente há duas formas de realizar UP dos containers, sendo elas realizadas através do “Docker Composer” ou diretamente através de imagens que estão localizadas no diretório “Docker Hub”.
O próximo passo consistiu no acesso ao container através do comando “docker exec -it nginx  /bin/bash” , também foi realizado a criação do “Proxy Reverso”  para redirecionar as requisições do nginx ao servidor do “IceCast”.
