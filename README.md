
# Desafio Icecast

Este repositório contém instruções para instalar e configurar o Icecast e o Nginx usando Docker. O Icecast é um serviço de streaming amplamente utilizado para transmissões de áudio e rádio, enquanto o Nginx pode ser usado para configurar um proxy reverso.

## 1. Instalação do Icecast via Docker

O Icecast é um serviço de streaming para transmissões de áudio e rádio, frequentemente utilizado em servidores GNU/Linux. Para iniciar o Icecast usando Docker, siga estas etapas:

1. **Executar o Container Icecast:**

   ```bash
   docker run --name icecast -p 8000:8000 --dns 8.8.8.8 --network bridge moul/icecast
