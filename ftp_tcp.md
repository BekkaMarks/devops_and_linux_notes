# FTP (File Transfer Protocol)

O **FTP** é um protocolo utilizado para transferência de arquivos entre computadores em uma rede baseada em **TCP/IP**.

Ele opera, geralmente, por meio de **duas conexões distintas**:

- **Canal de comando (control connection)**: responsável pelo envio de instruções e recebimento de respostas (ex.: autenticação, listagem de arquivos, solicitação de upload ou download).
- **Canal de dados (data connection)**: responsável pela transferência efetiva do conteúdo (arquivos ou listagens).

```text
                 (rede TCP/IP)
┌──────────────┐                 ┌────────────────────────┐
│ Cliente FTP  │                 │      Servidor FTP      │
│ (seu PC)     │                 │(onde ficam os arquivos)│
└──────┬───────┘                 └─────────┬──────────────┘
       │                                   │
       │ 1) CANAL DE COMANDO (controle)    │
       │    "login", "listar", "baixar"... │
       ├───────────────────────────────────►
       │ ◄─────────────────────────────────┤
       │    respostas: "ok", "erro", lista │
       │                                   |
       │ 2) CANAL DE DADOS (conteúdo real) │
       │    arquivos / listagens           │
       ├═════════════════════════════════► |  (download: servidor → cliente)
       │ ◄═════════════════════════════════┤  (upload: cliente → servidor)
```
### Fluxo de Funcionamento

1. O cliente inicia a conexão com o servidor.
2. O canal de comando permanece ativo durante toda a sessão, permitindo o envio de instruções e o recebimento de respostas.
3. Quando há necessidade de transferência, o canal de dados é aberto temporariamente para envio do conteúdo.
4. Após a conclusão, o canal de dados é encerrado, enquanto o canal de comando pode continuar ativo.

**Direção da transferência**: 📥 Download: servidor → cliente | 📤 Upload: cliente → servidor

- **Upload:** quando você envia um arquivo **do seu computador (cliente)** para um **servidor**.
- **Download:** quando você recebe um arquivo **do servidor** para o **seu computador (cliente)**.

## Servidor FTP

Um **servidor FTP** é um computador (ou serviço) configurado para **armazenar** e **disponibilizar arquivos** por meio do protocolo FTP. Ele permite o compartilhamento remoto de dados via internet (ou rede interna), atendendo solicitações de um **cliente FTP** (por exemplo, um programa como FileZilla ou um sistema que faça conexão via FTP).

De forma simples:
- **Servidor:** oferece os arquivos e controla permissões/acesso.
- **Cliente:** conecta, navega nas pastas e envia/baixa arquivos.
---

# TCP/IP (Transmission Control Protocol/Internet Protocol)

O FTP pertence à **camada de aplicação** e funciona sobre o conjunto de protocolos TCP/IP, base da comunicação na internet.

## Camadas

O modelo TCP/IP costuma ser organizado em camadas, por exemplo:

- **Aplicação:** onde ficam protocolos como **FTP**, HTTP, SMTP etc.
- **Transporte:** onde fica o **TCP** (e também o UDP).
- **Internet:** onde fica o **IP**, responsável por endereçamento e roteamento.
- **Acesso à rede:** camada ligada ao meio físico e à forma de acesso (Ethernet, Wi‑Fi etc.).

### Função de cada protocolo

- **TCP**: garante comunicação confiável, com controle de erros, ordenação e confirmação de entrega.
- **IP**: define o endereçamento e o roteamento dos pacotes na rede.
---
