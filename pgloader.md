# Visão Geral do Pgloader

O Pgloader nada mais é que um migrador e carregador de dados voltado ao PostgreSQL. Seu principal objetivo é transferir dados de diferentes origens de forma eficiente, automatizada e confiável.

Ele é capaz de transformar dados em tempo real durante a leitura, além de permitir a execução de comandos SQL antes e depois do carregamento. 
Internamente, o pgloader utiliza o protocolo <strong>COPY</strong> do PostgreSQL, que implementa um modelo de transmissão contínua (streaming), garantindo alto desempenho e melhor controle de erros.

Uma de suas principais vantagens é a capacidade de migrar dados diretamente de bancos de dados de origem, incluindo ambientes de produção, tratando schemas e dados em um único comando.
Esse modelo facilita migrações contínuas e reduz intervenções manuais.

## Modelos de Operação
- Carregamento de dados a partir de arquivos;
- Migração direta entre bancos de dados.

## Principais recursos
- Suporte a diversos formatos de origem, como CSV, arquivos de colunas fixas, dBase (db3) e IBM IXF 
- Transformação e limpeza de dados em tempo real 
- Projeção completa de campos 
- Leitura de arquivos compactados (zip, tar, gzip), com extração automática para diretórios temporários 
- Suporte a fontes HTTP e HTTPS 
- Descoberta automática do esquema de destino, adaptando-se a tabelas existentes e inferindo formatos como CSV 
- Controle de execução em caso de erro, permitindo parar ou continuar a partir da próxima etapa 
- Execução de comandos SQL antes e após o processo de carga
  
```Text
                                      ┌─────────────────────────┐
                                      │     Origem dos dados    │
                                      │    MySQL / CSV / HTTP   │
                                      └───────────┬─────────────┘
                                                  |  Leitura contínua
                                                  ▼
                                  ┌────────────────────────────────┐
                                  │           Pgloader             │
                                  |- Conversão de tipos e formatos |
                                  |- Mapeamento de schemas         |
                                  |- Execução via COPY (streaming) |
                                  |- Controle de erros             |
                                  └───────────────┬────────────────┘
                                                  |  COPY (streaming)
                                                  ▼
                                    ┌─────────────────────────┐
                                    │       PostgreSQL        │
                                    │       - Tabelas         |
                                    │       - Schemas         |
                                    └─────────────────────────┘
```
## Instalação

```bash
# Atualiza a lista de pacotes disponíveis no sistema
sudo apt update
# Instala o pgloader a partir dos repositórios oficiais
sudo apt install -y pgloader
# Acessa o PostgreSQL para validações iniciais
sudo -u postgres psql
```
