# Prometheus

``` bash
docker run -p 9090:9090 -v /portainer/Files/AppData/Config/Prometheus:/etc/prometheus prom/prometheus
```

\#/portainer/Files/AppData/Config/Prometheus/prometheus.yml

``` yaml
global:
scrape_interval: 15s
external_labels:
monitor: 'node'
scrape_configs:

- job_name: 'prometheus'
static_configs:
    - targets: ['10.0.0.23:9090'] ## pve3>CT104>docker>prometheus
- job_name: 'node-exporter'
static_configs:
    - targets: ['10.0.0.201:9100'] ## pve1
    - targets: ['10.0.0.203:9100'] ## pve3
```

