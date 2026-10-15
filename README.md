# Classdoor Infrastructure & DevOps

Este repositório centraliza toda a infraestrutura, scripts de automação, configurações de proxy e ferramentas de observabilidade do projeto **Classdoor**.

## 📂 Estrutura do Repositório

- **`/monitoring/`**: Stack de monitoramento baseada em Docker Compose (Grafana, Loki e Promtail) para coleta centralizada de logs dos serviços na VPS.
- **`/nginx/`**: Templates de configuração dos blocos de servidor do Nginx (Prod, Dev e Logs) que atuam como proxy reverso interno na VPS.

## 📊 Acesso ao Grafana Loki (Logs)
- **URL:** [https://logs.odominoapp.win](https://logs.odominoapp.win)
- **Credenciais de Acesso:** `<<SOLICITAR_AO_CTO_GABRIEL>>`
  *(Para obter o usuário e a senha administrativos do painel de logs, solicite diretamente ao CTO Gabriel-Aragao (`@domaragao`)).*

## 🌐 Arquitetura de Rede
O tráfego externo chega via **Cloudflare Tunnel**, bate no **Nginx** na porta 80 da VPS, que faz o roteamento interno baseado no subdomínio:
- `api.odominoapp.win` -> Produção (`localhost:8080`)
- `dev-api.odominoapp.win` -> Desenvolvimento (`localhost:8081`)
- `logs.odominoapp.win` -> Grafana (`localhost:3001`)
- `db.odominoapp.win` -> Banco PostgreSQL (`localhost:5432` via TCP Tunnel)
