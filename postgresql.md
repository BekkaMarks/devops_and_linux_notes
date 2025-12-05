# 🐘 Introdução ao PostgreSQL

PostgreSQL é um <strong>banco de dados relacional de código aberto</strong> que oferece suporte a recursos <strong>objeto-relacionais</strong>, como tipos definidos pelo usuário, herança e funções personalizadas.
Ele segue rigorosamente o modelo <strong>ACID</strong> (Atomicidade, Consistência, Isolamento e Durabilidade), garantindo segurança e integridade dos dados mesmo em cenários de falhas.

Para otimizar a recuperação de informações, o PostgreSQL utiliza <strong>índices</strong>, que nada mais são do que <strong>cópias organizadas de partes de uma tabela</strong>, permitindo buscas muito mais rápidas.
São semelhantes ao índice no final de um livro, que ajuda a encontrar um item sem precisar percorrer o livro inteiro.

O PostgreSQL oferece diferentes tipos de índices, como:
- <strong>B-tree</strong> (padrão e mais utilizado)
- <strong>Hash</strong>
- <strong>GIN</strong> (ideal para JSONB e arrays)
- <strong>GiST</strong>
- <strong>BRIN</strong> (ótimo para tabelas muito grandes)

O PostgreSQL usa descrições chamadas <strong>schemas</strong> para organizar a estrutura dos dados.
Um schema é o conjunto de tabelas, índices, funções e outros objetos dentro do banco de dados, e o PostgreSQL suporta múltiplos schemas sem conflito entre eles.

Além disso, o PostgreSQL é altamente <strong>extensível</strong>: é possível criar tipos de dados próprios, operadores, linguagens de função (como PL/pgSQL e PL/Python) e até instalar extensões como <strong>PostGIS</strong>.

Em cenários com múltiplos acessos simultâneos, o PostgreSQL gerencia a concorrência por meio do <strong>MVCC</strong> (Controle de Concorrência Multiversão).
Isso significa que:
- <strong>leituras não bloqueiam gravações</strong>, e
- <strong>gravações não bloqueiam leituras</strong>.

Esse modelo garante alto desempenho, reduz bloqueios e melhora o isolamento entre transações.

Outro componente fundamental é o <strong>WAL (Write-Ahead Logging)</strong>, um registro de todas as operações que garante durabilidade: antes de qualquer modificação ser escrita no disco, ela é registrada no WAL para que o banco possa ser recuperado em caso de queda inesperada.

O PostgreSQL conta ainda com diversos tipos de dados avançados, incluindo:
- <strong>JSON e JSONB</strong> (com performance excepcional)
- <strong>Arrays</strong>
- <strong>Tipos de faixa</strong> (range types)
- <strong>UUID</strong>
- <strong>Tipos geométricos</strong>

> <strong>Notas:</strong><br><br>
> MVCC — Recurso avançado de banco de dados que cria versões dos registros para permitir leitura e escrita simultâneas com segurança.
> Com o MVCC, vários usuários podem consultar e modificar dados ao mesmo tempo sem comprometer a integridade do banco.
> Principais vantagens:
> - Cria versões dos registros para leitura e escrita simultâneas
> - Evita bloqueios entre leituras e gravações
> - Mantém isolamento entre transações
> - Melhora o desempenho em ambientes com muitos usuários
> 
> B-tree — Estrutura de índice baseada em árvore balanceada. Mantém os dados organizados de forma ordenada, permitindo buscas rápidas mesmo em tabelas grandes. É o tipo de índice padrão no PostgreSQL por ser eficiente na maioria das consultas.<br>
> Estrutura Interna:<br>
> - Nó Raiz: ponto inicial da busca; contém chaves que direcionam para outros nós.
> - Nós Internos: organizam as chaves e definem o caminho até os dados; funcionam como intermediários.
> - Nós Folha: armazenam as chaves indexadas e ponteiros para as linhas da tabela.
> - Balanceamento: quando um nó enche, ele se divide; isso mantém a árvore sempre rasa e rápida para buscar.
> 
> Hash — Índice baseado em funções de hash, ideal para comparações de igualdade (=).
> Cria um valor hash para cada chave e acelera buscas onde não importa a ordem dos dados.
> Mais eficiente que B-tree em consultas que usam igualdade pura, mas não serve para ordenação nem intervalos.
> 
> GIN (Generalized Inverted Index) — Índice otimizado para armazenar múltiplos valores por linha, como arrays, JSONB e documentos de texto.
> Excelente para buscas que envolvem contém, pertence ou existem estas chaves.
> Muito usado em colunas JSONB com operadores como @>, ? e ?|.
> 
> GiST (Generalized Search Tree) — Estrutura flexível que permite indexar dados complexos, como valores geométricos, textos aproximados e tipos personalizados.
> Não armazena necessariamente em ordem, mas cria uma árvore de regiões que facilita buscas por similaridade, proximidade e interseção.
> Base de índices como pg_trgm e PostGIS.
> 
> BRIN (Block Range Index) — Índice leve que armazena apenas metadados sobre blocos de dados, não valores individuais.
> Ideal para tabelas enormes onde os dados são naturalmente ordenados, como logs, timestamps e séries temporais.
> Muito pequeno e rápido de criar, com grande ganho de desempenho em buscas por faixa.






<br><br>

<h3>Referências Utilizadas na Construção deste Material:</h3> 
https://cloud.google.com/discover/what-is-postgresql <br> 
https://www.ibm.com/think/topics/postgresql <br> 
https://aws.amazon.com/pt/compare/the-difference-between-mysql-vs-postgresql/ <br> 
https://www.postgresql.org/download/linux/ubuntu/ <br> 
https://www.hostinger.com/br/tutoriais/instalar-postgresql-ubuntu <br> 
https://www.vivaolinux.com.br/dica/Instalando-o-servidor-PostgreSQL-no-Linux <br> 
https://serverspace.com.br/support/glossary/mvcc/ <br>
https://serverspace.com.br/support/glossary/b-tree/ <br>
https://pt.stackoverflow.com/questions/101065/o-que-s%C3%A3o-os-%C3%ADndices-b-tree-hash-gist-e-gin <br>
