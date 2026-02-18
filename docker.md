# Docker - Guia Básico

## O que é docker? 

Serviço de virtualização que permite criar aplicações independentes do ambiente onde estamos desenvolvendo, possibilitando o deploy contendo todas as dependências necessárias para a execução da aplicação.

O Docker pega a aplicação e a coloca dentro de um container. Esse container é independente dos outros processos que estão rodando em nossa máquina.

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
