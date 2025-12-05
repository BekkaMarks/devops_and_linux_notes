# 🐘 Introdução ao PostgreSQL

PostgreSQL é um <strong>banco de dados relacional de código aberto</strong> que oferece suporte a recursos <strong>objeto-relacionais</strong>, como tipos definidos pelo usuário, herança e funções personalizadas.

Para otimizar a recuperação de informações, o PostgreSQL utiliza <strong>índices</strong>, que nada mais são do que <strong>cópias organizadas de partes de uma tabela</strong>, permitindo uma busca muito mais rápida.
São semelhantes a um índice no final de um livro, que ajuda a encontrar um item sem precisar percorrer o livro inteiro.

O PostgreSQL usa descrições chamadas <strong>schemas</strong> para organizar a estrutura dos dados.
Um schema é o conjunto de tabelas, índices e funções dentro do banco de dados, e o PostgreSQL suporta múltiplos schemas em um mesmo banco.

Em cenários com múltiplos acessos simultâneos, o PostgreSQL gerencia a concorrência de forma eficiente por meio do MCVV (Controle de Concorrência Multiversão).
Isso significa que:

- <strong>as leituras não bloqueiam as gravações, e</strong>
- <strong>as gravações não bloqueiam as leituras.</strong>

Esse modelo garante maior desempenho e evita bloqueios desnecessários.

><strong>Notas:</strong><br><br>
>MCVV - Recurso avançado de banco de dados que cria versões dos registros para permitir leitura e escrita simultâneas com segurança.
>Com o MVCC, vários usuários podem consultar e modificar dados ao mesmo tempo sem comprometer a integridade do banco.<br>
>Principais vantagens:
> - Cria versões dos registros para leitura e escrita simultâneas
> - Evita bloqueios entre leituras e gravações
> - Mantém isolamento entre transações
> - Melhora o desempenho em ambientes com muitos usuários

<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://cloud.google.com/discover/what-is-postgresql <br>
https://www.ibm.com/think/topics/postgresql <br>
https://aws.amazon.com/pt/compare/the-difference-between-mysql-vs-postgresql/#:~:text=O%20controle%20de%20simultaneidade%20multivers%C3%A3o,oferece%20suporte%20a%20esse%20recurso. <br>
https://www.postgresql.org/download/linux/ubuntu/ <br>
https://www.hostinger.com/br/tutoriais/instalar-postgresql-ubuntu <br>
https://www.vivaolinux.com.br/dica/Instalando-o-servidor-PostgreSQL-no-Linux <br>
https://serverspace.com.br/support/glossary/mvcc/ <br>
