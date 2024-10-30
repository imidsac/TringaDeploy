# README

# Docker Network
docker network create tringa_app

# NGINX+LetsEncrypt
```shell
docker-compose build
docker-compose up -d

docker-compose stop
docker-compose start
```

# Rails
```shell
docker build -t app ./Tringa/.
docker volume create tringaapp-storage
docker run -d --rm -it --name tringa --env-file ./Tringa/.env -v tringaapp-storage:/rails/storage --network tringa_app tringaapp
```

# Another Rails
```shell
docker build -t another_app ./another/.
docker volume create app-storage
docker run -d --rm -it --name another --env-file ./another/.env -v app-storage:/rails/storage --network everything_app another_app
```

# Postgres
```shell
mkdir psql/postgres-data
docker build -t psql ./psql/.
docker run -d --name postgres --env-file ./psql/.env -v postgres-data:/var/lib/postgresql/data --network tringa_app psql
