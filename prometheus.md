# Introdução ao Prometheus

Prometheus é uma ferramenta de monitoramento que coleta métricas em tempo real de serviços e sistemas, armazena os dados em um banco de séries temporais e permite criar alertas e dashboards para acompanhar o desempenho da infraestrutura.

### Características:

- Modelo multi-dimensional
> Funciona permitindo que cada métrica tenha labels (rótulos) que adicionam contexto e permitem consultas mais detalhadas e flexíveis.
> Introdução ao Prometheus

- Independência entre servidores
> Prometheus não depende de armazenamento distribuído; cada instância opera de forma isolada, o que simplifica a arquitetura e evita acoplamentos complexos.

- Modelo HTTP pull para coleta
> O Prometheus coleta métricas buscando periodicamente informações nos alvos (targets) através do protocolo HTTP — um fluxo baseado em pull, onde o próprio servidor inicia a coleta.

- Envio de métricas via gateway para trabalhos em lote
> Para cenários em que não é possível expor um endpoint contínuo (como scripts de curta duração ou jobs em lote), o Prometheus suporta o envio de séries temporais por meio do Pushgateway, um componente intermediário.

- Descoberta de alvos
> As aplicações monitoradas podem ser encontradas por:<br>
> - descoberta de serviço (como Kubernetes, Consul, EC2), ou<br>
> - configuração estática, definida diretamente no arquivo prometheus.yml.

- Suporte a gráficos e painéis
> Embora o Prometheus possua uma interface básica para consultas, ele se integra facilmente a ferramentas como Grafana para visualizações mais avançadas.

- Federação hierárquica e horizontal
> O Prometheus permite que uma instância consulte métricas de outras instâncias, criando uma federação. Isso facilita:<br>
> - consolidação de métricas entre ambientes;<br>
> - escalabilidade horizontal;<br>
> - agrupamento de dados provenientes de diferentes regiões ou clusters.

- Linguagem própria (PromQL) para queries de dados em formato <i>time series</i>
> Time series (série temporal) é um conjunto de valores registrados ao longo do tempo, cada ponto contendo:<br>
>  - um instante (timestamp);<br>
>  - um valor numérico;<br>
>  - (no Prometheus) um conjunto de labels;<br>
> Exemplo: quantidade de requisições HTTP por segundo — registrada a cada 5 segundos.
















<br><br>
<h3>Referências Utilizadas na Construção deste Material:</h3>
https://github.com/prometheus/prometheus
https://medium.com/techbloghotmart/o-que-s%C3%A3o-s%C3%A9ries-temporais-e-como-aplicar-em-machine-learning-6ea5d94bec78
https://blog.4linux.com.br/primeiros-passos-com-promql/
https://medium.com/@habbema/introdu%C3%A7%C3%A3o-ao-prometheus-8ae1cd56ca97
