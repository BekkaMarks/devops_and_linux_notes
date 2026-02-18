# Docker - Guia Básico

## O que é docker? 

Docker é uma plataforma de <strong>containerização</strong> que permite empacotar uma aplicação junto com todas as suas dependências (bibliotecas, configurações, runtime etc.), garantindo que ela funcione da mesma forma em qualquer ambiente.

O Docker executa a aplicação dentro de um container, que é um ambiente isolado dos demais processos da máquina, mas que compartilha o kernel do sistema operacional.

## Docker vs Máquinas Virtuais

### Principais Diferenças

| Aspecto | Máquina Virtual | Docker Container |
|---------|----------------|------------------|
| **Sistema Operacional** | Cada VM tem seu próprio SO completo | Compartilha o kernel do SO hospedeiro |
| **Tamanho** | Gigabytes (inclui SO inteiro) | Megabytes (apenas app + dependências) |
| **Inicialização** | Minutos | Segundos |
| **Desempenho** | Overhead significativo | Quase nativo |
| **Isolamento** | Isolamento completo via hardware | Isolamento via namespaces e cgroups |
| **Portabilidade** | Menos portável (depende do hypervisor) | Altamente portável |

### Como o Docker Funciona

O Docker utiliza recursos nativos do kernel Linux para criar isolamento:

- **Namespaces**: Isolam a visão que cada container tem do sistema
  - PID: Isolamento de processos
  - NET: Isolamento de rede
  - MNT: Isolamento de sistema de arquivos
  - UTS: Isolamento de hostname
  - IPC: Isolamento de comunicação entre processos

- **Cgroups (Control Groups)**: Limitam e controlam os recursos disponíveis
  - CPU
  - Memória RAM
  - I/O de disco
  - Largura de banda de rede

 **Vantagem**: Como os containers compartilham o kernel do SO hospedeiro, a operação é muito mais leve e eficiente. Uma única máquina física pode executar dezenas ou centenas de containers simultaneamente.
 
## Conceitos Fundamentais

### DockerFiles
Arquivos que estão dentro da aplicação e funcionam como o projeto da arquitetura da aplicação para que ela funcione de forma adequada. Contêm todas as informações necessárias para gerar a imagem do Docker.

### Containers
Instância de uma imagem em execução.

### Imagens
Contêm as informações do ambiente (sistema de arquivos, dependências, configurações).

### Registros
Hubs que concentram imagens do Docker, utilizados para armazenar e reutilizar imagens. O mais conhecido é o [Docker Hub](https://hub.docker.com/).

## Comandos Essenciais
| Descrição | Comando |
|-----------|---------|
| Listar containers em execução | `docker ps` |
| Listar todos os containers (incluindo parados) | `docker ps -a` |
| Executar um container a partir de uma imagem | `docker run <imagem>` |
| Executar em modo interativo com terminal | `docker run -it <imagem> /bin/bash` |
| Executar em background (modo detached) | `docker run -d <imagem>` |
| Executar com mapeamento de portas (host:container) | `docker run -p 8080:80 <imagem>` |
| Executar com nome personalizado | `docker run --name meu-container <imagem>` |
| Parar um container em execução | `docker stop <container_id ou nome>` |
| Iniciar um container parado | `docker start <container_id ou nome>` |
| Reiniciar um container | `docker restart <container_id ou nome>` |
| Remover um container (precisa estar parado) | `docker rm <container_id ou nome>` |
| Forçar remoção de um container em execução | `docker rm -f <container_id ou nome>` |
| Executar comandos dentro de um container em execução | `docker exec -it <container_id> /bin/bash` |
| Ver logs de um container | `docker logs <container_id>` |
| Ver logs em tempo real | `docker logs -f <container_id>` |
| Inspecionar detalhes de um container | `docker inspect <container_id>` |
| Ver estatísticas de uso de recursos | `docker stats` |

### Gerenciamento de Imagens

| Descrição | Comando |
|-----------|---------|
| Listar imagens locais | `docker images` |
| Baixar uma imagem do registro | `docker pull <imagem>:<tag>` |
| Construir uma imagem a partir de um Dockerfile | `docker build -t <nome-da-imagem>:<tag> .` |
| Construir sem usar cache | `docker build --no-cache -t <nome-da-imagem> .` |
| Remover uma imagem | `docker rmi <image_id ou nome>` |
| Remover imagens não utilizadas | `docker image prune` |
| Ver histórico de camadas de uma imagem | `docker history <imagem>` |
| Enviar imagem para um registro | `docker push <usuario>/<imagem>:<tag>` |
| Criar tag para uma imagem | `docker tag <imagem-origem> <nova-imagem>:<tag>` |

### Gerenciamento de Volumes

| Descrição | Comando |
|-----------|---------|
| Listar volumes | `docker volume ls` |
| Criar um volume | `docker volume create <nome-volume>` |
| Inspecionar um volume | `docker volume inspect <nome-volume>` |
| Remover um volume | `docker volume rm <nome-volume>` |
| Executar container com volume | `docker run -v <nome-volume>:/caminho/no/container <imagem>` |

### Limpeza e Manutenção

| Descrição | Comando |
|-----------|---------|
| Remover todos os containers parados | `docker container prune` |
| Remover todas as imagens não utilizadas | `docker image prune -a` |
| Remover todos os volumes não utilizados | `docker volume prune` |
| Limpeza geral (containers, imagens, volumes, redes) | `docker system prune` |
| Limpeza completa incluindo volumes | `docker system prune -a --volumes` |
| Ver espaço em disco usado pelo Docker | `docker system df` |
