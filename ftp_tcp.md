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

# Como criar um servidor FTP
Antes de iniciar a configuração do FTP, é necessário instalar o serviço responsável pelo protocolo.

O pacote a ser utlizado será o **VSFTPD (Very Secure FTP Daemon)**.

**1. Atualizar repositórios** 
```bash
sudo apt-get update
```
**2. Instalando VSFTPD** 
```bash
sudo apt-get install vsftpd
```
**3. Backup do arquivo de configuração**<br>
Antes de realizar qualquer alteração, é uma boa prática criar uma cópia de segurança do arquivo original:
```bash
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.orig
```
**4. Liberar portas no firewall** <br>
O FTP utiliza as seguintes portas padrão:
- 20/TCP → Transferência de dados
- 21/TCP → Controle da conexão <br>
Para liberar no firewall (caso esteja utilizando o UFW):
```bash
sudo ufw allow 20/tcp
sudo ufw allow 21/tcp
```
⚠️ Observação: Se o servidor estiver atrás de roteador ou firewall externo, pode ser necessário liberar as portas também no equipamento de rede.

**5. Verificar o usuário FTP do sistema**
```bash
cat /etc/passwd | grep ftp
```
**6. Criando Usuáros para acesso FTP** <br>
Para permitir acesso ao servidor FTP de forma controlada, recomenda-se criar um usuário específico para esse fim.
```bash
sudo adduser usuario_acesso
```
**7. Criando Diretório para armazenamento FTP** <br>
Após criar o usuário, é recomendável criar um diretório dedicado para armazenar os arquivos que serão acessados via FTP:
```bash
sudo mkdir /home/usuario_acesso/ftp
```
**8.Ajustando Permissões para ambiente seguro (Chroot)** <br>
***Criar diretório para upload***
```bash
sudo mkdir /home/usuario_acesso/ftp/files
```
Esse diretório será usado para armazenar os arquivos enviados via FTP.

***Alterar proprietário da pasta raiz do FTP***
```bash
sudo chown nobody:nogroup /home/usuario_acesso/ftp
```
Isso é feito porque quando utilizamos chroot_local_user=YES, o VSFTPD não permite que o diretório raiz seja gravável pelo usuário por motivos de segurança.

***Remover Permissões de escrita da pasta raiz***
```bash
sudo chmod a-w /home/usuario_acesso/ftp
```
O VSFTPD exige que a raiz do chroot não seja gravável.

***Verificar Permissões***
```bash
sudo ls -la /home/usuario_acesso/ftp
```
**9. Ajustar Permissões da pasta de Upload** <br>
Após configurar o diretório raiz do FTP para não ser gravável (exigência do chroot do vsftpd), é necessário garantir que o usuário tenha permissão de escrita na subpasta destinada aos uploads.

```bash
sudo chown usuario_acesso:usuario_acesso /home/usuario_acesso/ftp/files
```

**10. Criar Arquivo teste** <br>
Para validar se as permissões estão corretas, podemos criar um arquivo de teste:
```
echo "vsftpd test file" | sudo tee /home/usuario_acesso/ftp/files/test.txt
```

**11. Removendo o arquivo de configuração padrão** <br>
Como foi realizado backup anteriormente, podemos remover o arquivo original para criar uma nova configuração do zero:
```bash
sudo rm /etc/vsftpd.conf
```
⚠️ Atenção: Só execute esse comando se o backup já tiver sido criado.

**12. Verificando ou Escolhendo o Editor de Texto** <br>
Antes de criar o novo arquivo de configuração do vsftpd, é recomendável verificar qual editor de texto está configurado como padrão no sistema.
```bash
sudo update-alternatives --display editor
```
***(Opcional) Alterar Editor Padrão*** <br>
Caso deseje escolher outro editor instalado:
```bash
sudo update-alternatives --config editor
```
***(Opcional) Instalar Outro Editor*** <br>
Se o editor desejado não estiver instalado, você pode instalá-lo manualmente.
Instalar o Nano
```bash
sudo apt-get install nano
```
Instalar o Vim
```bash
sudo apt-get install vim
```

Após instalar, execute novamente para defini-lo como padrão:
```bash
sudo update-alternatives --config editor
```

**13. Criar Novo Arquivo de Configuração do VSFTPD** <br>
Agora crie o novo arquivo utilizando o editor de sua preferência.<br>
Com o comando nano:
```bash
sudo nano /etc/vsftpd.conf
```
Com o comando VI/VIM
```bash
sudo vi /etc/vsftpd.conf
```
***Inserir o Conteúdo no Arquivo***
```bash
listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
force_dot_files=YES
allow_writeable_chroot=YES
```

**14. Adicionar Usuário à Lista de Permitidos** <br>
Agora adicione o usuário criado anteriormente (usuario_acesso) à lista de usuários permitidos:
```bash
echo "usuario_acesso" | sudo tee -a /etc/vsftpd.userlist
```
Se o arquivo /etc/vsftpd.userlist não existir, ele será criado automaticamente.

**15. Reiniciar o Serviço FTP** <br>
Para aplicar as configurações:
```bash
sudo systemctl restart vsftpd
```
Verifique se o serviço está ativo:
```bash
sudo systemctl status vsftpd
```

## 📚 Referências
- 📘 [Entendendo logs FTP](https://blog.ironlinux.com.br/entendendo-logs-ftp/)
- 💻 [Comando Linux FTP](https://sempreupdate.com.br/comando-linux-ftp-domine-a-transferencia-de-arquivos-pelo-terminal/)
- 🌐 [O que é FTP e como funciona](https://www.hostinger.com/br/tutoriais/ftp-o-que-e-como-funciona)
-  [Tutorial Prático: Criar servidor FTP no Linux com VSFTP](https://www.vivaolinux.com.br/dica/VSFTP-no-Ubuntu-Instalacao-e-Configuracao/)
- 📡 [O que é TCP/IP](https://tecnoblog.net/responde/o-que-e-tcp-ip/)
