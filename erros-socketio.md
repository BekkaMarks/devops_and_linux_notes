# 🛠️ Possíveis Soluções para Problemas com SocketIO

Este guia tem o objetivo de auxiliá-lo caso ocorra algum erro relacionado ao SocketIO. Lembre-se de que esses erros podem ter diversas causas; portanto, analise cada situação para identificar a melhor solução.
Caso encontre uma correção diferente das listadas aqui, registre-a juntamente com a documentação de referência. Assim, centralizamos o conhecimento e facilitamos o suporte para outras pessoas.<br>

- <strong>1 Possível resolução (hosts)</strong><br>
Primeiro, verifique o status do "SocketIO Ping Check" no sistema: acesse Help → System Health.
Se o status estiver como Fail, significa que algum problema está ocorrendo.
Máquinas hospedadas no Proxmox sempre iniciam sem o IP configurado no arquivo /etc/hosts, sendo necessário adicioná-lo manualmente.<br>

Para obter o IP interno da máquina, execute:
```bash
hostname -I
```
Ou, para mais detalhes:
```bash
ip a s
```

Edite o arquivo /etc/hosts e adicione na última linha:
```bash
sudo nano /etc/hosts
```
```bash
<ip-interno> <dominio-do-site>
Ex: 10.0.0.15   meu-site.local
```

Regere as configurações de produção:
```bash
sudo bench setup production frappe
```
Após a alteração, teste novamente e verifique se o status do "SocketIO Ping Check" mudou para Pass.

## Realtime (SocketIO) no Frappe 16
1. Verificar os serviços registrados no Supervisor:
    ```bash
   sudo supervisorctl status
   ``` 
2. Regerar os arquivos de configuração do Supervisor a partir do Bench:
   ```bash
   bench setup supervisor
   ```
3. Aplicar as alterações no Supervisor:
   ```bash
   sudo supervisorctl update
   ```
4. Confirmar se o serviço node-socketio foi criado e está em execução:
   ```bash
   sudo supervisorctl status
   ```
