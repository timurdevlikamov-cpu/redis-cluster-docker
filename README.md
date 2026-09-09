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

docker exec -it redis-node-0 redis-cli --cluster create \
redis-node-0:6379 \
redis-node-1:6379 \
redis-node-2:6379 \
redis-node-3:6379 \
redis-node-4:6379 \
redis-node-5:6379 \
--cluster-replicas 1
```

### Проверка статус кластера
```bash
docker ps

docker exec -it redis-node-0 redis-cli cluster nodes

docker exec -it redis-node-0 redis-cli cluster info
```
