# Grafana

Grafana é uma plataforma de visualização e análise de dados que unifica métricas, logs e traces a partir de diversas fontes. Ele renderiza dashboards interativos, executa consultas e oferece recursos de alertas e automações.

Observabilidade
- O que oferece: exploração ad-hoc, análise de correlação entre métricas, logs e traces (via Prometheus, Loki, Tempo, Mimir etc.) e suporte à investigação de causa raiz.
- Como funciona: conecta-se a data sources, permitindo consultar séries temporais, logs e rastreamentos, relacionar visualmente eventos e entender comportamentos inesperados no sistema.

Monitoramento
- O que oferece: dashboards operacionais, acompanhamento em tempo real e alertas configuráveis para detectar condições conhecidas (thresholds, SLAs, KPIs).
- Como funciona: consulta métricas e logs fornecidos por ferramentas especializadas (ex.: Prometheus, InfluxDB, Loki) e exibe tendências, status e gatilhos de alerta para o dia a dia das operações.

Em suma: Grafana serve tanto ao monitoramento (detecção e notificação) quanto à observabilidade (investigação e correlação), sendo extensível e utilizável on‑premises ou na nuvem.
<br><br>

<h3>Referências Utilizadas na Construção deste Material:</h3>
https://github.com/grafana/grafana
https://www.redhat.com/pt-br/topics/data-services/what-is-grafana
https://blog.updev.dev.br/posts/grafana-a-plataforma-aberta-para-monitoramento-e-observabilidade
