## MariaDB 
É um sistema de gerenciamento de banco de dados relacional (RDBMS), de código aberto e com suporte a multithreading. Oferece alta performance, mecanismos de armazenamento flexíveis e total compatibilidade com o MySQL.
Destaca-se também por sua segurança, suporte a JSON e fácil escalabilidade.

### Variáveis e suas funcionalidades

#### ➜ <strong>InnoDB Buffer Pool</strong>
O InnoDB Buffer Pool é uma área de memória de tamanho fixo, configurada por meio do parâmetro <code>innodb_buffer_pool_size</code>. 
Ele é responsável por armazenar em cache páginas de dados, páginas de índices e metadados, com o objetivo de reduzir operações de leitura e escrita em disco, melhorando o desempenho do banco de dados.

#### ➜ <strong>InnoDB Redo Log</strong>
Responsável por registrar as alterações realizadas nos dados antes de serem persistidas no disco, garantindo integridade e recuperação em caso de falhas.<br>
- <code>innodb_log_file_size</code>: define o tamanho de cada arquivo de log.<br>
- <code>innodb_log_files_in_group</code>: define a quantidade de arquivos de log utilizados em conjunto.
- <code>innodb_log_buffer_size</code>: define o tamanho do buffer em memória utilizado para armazenar temporariamente as alterações antes de serem gravadas nos arquivos de log.

#### Tabelas temporárias
São tabelas criadas automaticamente pelo MariaDB durante a execução de uma query, para armazenar dados intermediários.<br><br>
É importante observar a quantidade de tabelas temporárias que estão sendo criadas em disco. Caso esse percentual esteja acima de 20% a 25%, pode haver impacto negativo na performance.

Nesses casos, algumas ações podem ser tomadas:
   - Aumentar o valor da variável @@tmp_table_size
   - Analisar as queries executadas, verificando se estão otimizadas e performáticas
     
><strong>Notas:</strong><br><br>
> Multithreading: É uma técnica de programação onde um programa executa várias tarefas (threads) ao mesmo tempo dentro do mesmo processo.
