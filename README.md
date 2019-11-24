# nginx-prometheus-grafana-fiap  
Trabalho de Sre da fiap, neste projeto estamos subindo o nginx com uma pagina qualquer e monitorando com prometheus e criando graficos no grafana  


Como subir (ainda em construção):  
Criando imagem personalizada do nginx (usado o Dockerfile, onde index é uma saudação e o health tem uma msg de ok): 

Rodando o container 
docker run -d -p 8080:80 nginx_vitor:latest



Nginx to prometheus exporter  

docker run -d -p 9113:9113 nginx/nginx-prometheus-exporter:0.4.2 -nginx.scrape-uri http://18.219.219.70:8080/metrics -nginx.retries=10 -web.telemetry-path=/prometheus


Subindo o prometheus onde o conteúdo do yml está abaixo:  
scrape_configs:  
"""
  - job_name: 'nginx-vitor'
    scrape_interval: 1m
    metrics_path: '/prometheus'
    static_configs:
      - targets: ['18.219.219.70:9113']
"""

Comando para Subir  
docker run -d -p 9090:9090 -v /home/ubuntu/nginx/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

Subindo o Grafana  
docker run -d -p 3000:3000 grafana/grafana

Adicionando métricas e graficos no grafana (falta descrever): 
-
-

## Bibliografia
https://medium.com/@wilsonjnior/escutando-os-quatro-sinais-de-ouro-do-sre-usando-nginx-prometheus-grafana-6f2b7f9577dc
https://github.com/wpjunior/nginx-vts


https://dimitr.im/monitoring-nginx-with-prometheus-and-grafana
https://github.com/nginxinc/nginx-prometheus-exporter

http://nginx.org/en/docs/http/ngx_http_stub_status_module.html

https://hub.docker.com/_/nginx?tab=description
