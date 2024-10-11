## Config Entorno de desarrollo

## Local

```
docker-compose -p services -f ./local.yml up -d
docker-compose -p services -f ./local.yml down

docker compose -p services -f ./dev.yml up -d
docker compose -p services -f ./dev.yml down

docker-compose -p services -f ./haproxy.yml up -d
docker-compose -p services -f ./haproxy.yml down
```

## Deploy

```
docker network create proxy

docker-compose -p services -f ./prd.yml up -d
docker-compose -p services -f ./prd.yml down

docker system prune -a --volumes -f
```

## QA

```
mkdir redis
mkdir redis/data

mkdir nats
mkdir nats/data

docker compose -p services -f ./qa.yml down
docker compose -p services -f ./qa.yml up -d

docker build -t haproxy-with-tools .
docker run -it haproxy-with-tools /bin/sh

docker cp postgres-master:/etc/postgresql/postgresql.conf .
```

Connection failed: The connection attempt failed. (jdbc:postgresql://localhost:5435/test using org.postgresql.Driver)

## Description

```
git backup
git update
git new <name a brach>
```
