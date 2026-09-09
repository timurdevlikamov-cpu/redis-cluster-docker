# Развертывание Redis Cluster из 3 шардов и 3 реплик
Схема:

![Скрин](114282923-9b16f900-9a4f-11eb-80aa-61ed09725760.png)

### Предварительные требования
- Docker Engine >= 20.0
- Docker Compose

### Запуск кластера
```bash
mkdir redis-cluster-docker
cd redis-cluster-docker

docker compose up -d

docker exec -it redis-cluster-docker-redis-node-0-1 redis-cli --cluster create \
redis-cluster-docker-redis-node-0-1:6379 \
redis-cluster-docker-redis-node-1-1:6379 \
redis-cluster-docker-redis-node-2-1:6379 \
redis-cluster-docker-redis-node-3-1:6379 \
redis-cluster-docker-redis-node-4-1:6379 \
redis-cluster-docker-redis-node-5-1:6379 \
--cluster-replicas 1
```

### Проверка статус кластера
```bash
docker ps 
docker exec -it redis-node-0 redis-cli cluster nodes
docker exec -it redis-node-0 redis-cli cluster info
```
