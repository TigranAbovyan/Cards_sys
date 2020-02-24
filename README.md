# Cards_sys

With this command we are creating docker network
```
docker network create --driver bridge --subnet 172.18.0.0/16 --gateway 172.18.0.1 docker-network
```
Running Prometheus.yml file
```
docker run --name prometheus -d -p 9090:9090 -v /etc/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus --config.file="/etc/prometheus/prometheus.yml" 
```
Connecting to docker connect
```
docker network connect --ip 172.18.0.2 docker-network prometheus
```
```
docker run --name node -d -p 9100:9100  prom/node-exporter
```
```
docker network connect --ip 172.18.0.3 docker-network node
```
```
http://localhost:9090/
```
