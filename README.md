# docker-study

- Steps to replicate this Lab:

```
$ docker ps

$ docker ps -a

$ docker run postgres

$ docker run -e POSTGRES_PASSWORD=password postgres:11.20-alpine

$ docker pull ubuntu

$ docker rm [ID]

$ docker exec -it [ID] sh

$ docker logs -f [ID]

$ docker build -t getting-started .

$ docker images
```

```
$ docker run getting-started

$ docker stop [ID]

$ docker run -dp 3000:3000 getting-started

$ docker stop [ID]

$ docker -v /path/in/host:/etc/todos -p 3000:3000 -d getting-started
```

## can be now removed and created again, contents will remain in host:container bidirectionally.
## makes changes in image and build again

```
$ docker build -t getting-started:v2 .

$ docker login
$ docker images
$ docker tag 79a2969823ea wusted/getting-started:v2
$ docker images
$ docker push wusted/getting-started:v2
```

## Persistent Volume, 2 docker container, 1 for Database and 1 for Web App.
```
$ docker network create todo-app
$ docker network ls
$ docker run -d --network todo-app --network-alias mysql -v /Users/jpereira/Git\ Projects/docker-study/multi-container/todo-mysql-data:/var/lib/mysql --platform linux/x86_64 -e MYSQL_ROOT_PASSWORD=pass -e MYSQL_DATABASE=todos mysql:5.7

$ docker ps
$ docker exec -it 28385917b486 mysql -p
$ docker run -it --network todo-app nicolaka/netshoot

$ docker run -dp 3000:3000 --network todo-app -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=pass -e MYSQL_DB=todos getting-started:v2
$ docker ps
$ docker logs [ID]
```

# Docker Compose
```
$ docker-compose up -d
$ docker ps
$ docker compose down
$ docker ps
```


