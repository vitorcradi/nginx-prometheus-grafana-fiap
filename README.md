# nginx-prometheus-grafana-fiap  
Trabalho de Sre da fiap, neste projeto estamos subindo o nginx com uma pagina qualquer e monitorando com prometheus e criando graficos no grafana  

### Componentes:
Os componentes do Projeto são 4 containeres:
1. nginx com uma página de bem vindo com as métricas expostas na pasta /metrics
2. nginx-prometheus-exporter para capturar as métricas do serviço web acima e disponibilizar para o Prometheus
3. o serviço do prometheus
4. o serviço do Grafana

### Como subir:  
1. Baixar este projeto (git clone https://github.com/vitorcradi/nginx-prometheus-grafana-fiap.git)
2. entrar na pasta nginx-prometheus-grafana-fiap
3. executar o comando "docker-compose up" (ou "docker-compose up -d" se quiser deixar os serviços rodando em seguindo plano)

### Acessos:
Web - http://localhost:8080/  
Web Health check - http://localhost:8080/health  
Prometheus - http://localhost:9090/targets  
Grafana - http://localhost:3000/  


### Adicionando métricas e graficos no grafana: 
1. Acessar a url do Grafana acima
2. Entrar com usuário e senha (admin e admin)
3. Adicionar o Data Source do Prometheus, adicionando esta URL: http://host.docker.internal:9090
4. Clicar em Save & Test e depois em back
5. Na página Principal passar o mouse em Dashboard e clicar em Manage
6. Clicar no botão "import" (ao lado do botão "New Dashboard" e "New Folder")
7. Clicar em "upload .json file"
8. Selecionar o arquivo Nginx_Dashboard.json
9. Trocar o nome se quiser e clicar em "import"

Faça alguns requests na página web de bemvindo e observe o gráfico recebendo métricas.


## Bibliografia
https://medium.com/@wilsonjnior/escutando-os-quatro-sinais-de-ouro-do-sre-usando-nginx-prometheus-grafana-6f2b7f9577dc
https://github.com/wpjunior/nginx-vts


https://dimitr.im/monitoring-nginx-with-prometheus-and-grafana
https://github.com/nginxinc/nginx-prometheus-exporter

http://nginx.org/en/docs/http/ngx_http_stub_status_module.html

https://hub.docker.com/_/nginx?tab=description
