# Node-Exporter

``` bash 
apt-get update
apt-get install docker-ce docker-ce-cli containerd.io
```

## VM

``` bash
docker run -d --net="host" --pid="host" -v "/:/host:ro,rslave" quay.io/prometheus/node-exporter:latest --path.rootfs=/host
```

## UNRAID

``` bash
docker run -d --name="node-exporter" --net="host" --pid="host" prom/node-exporter
```

