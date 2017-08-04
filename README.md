# Docker

## Build a Node App With Postgres and Docker ELECTIVES

Source Code: https://github.com/codeschool/WatchUsBuild-SimpleNodeAppWithDocker

Video: https://www.codeschool.com/screencasts/build-a-node-app-with-postgres-and-docker


## Commands

```
docker pull nginx

docker images

docker ps

docker stop SHA

docker container run nginx:latest

docker container run -p 9999:80 nginx:latest

docker container run -p 9999:80 --name web-server nginx:latest

docker exec -it web-server /bin/bash

cd /usr/share/nginx/html

touch page.html

apt-get update

apt-get install -y nano


docker ps --all

docker rm web-server

docker container run -p 9999:80 --name web-server --rm nginx:latest

docker container run -p 9999:80 --name web-server --rm -v ~/Desktop/Docker/VolumnName/nginx/html:/usr/share/nginx/html nginx nginx:latest
```


## Dockerfile
Save the following as `Dockerfile`

```
FROM nginx:latest
EXPOSE 80
RUN apt-get update && apt-get install -y nano
LABEL maintainer="abc@example.com"
VOLUMN /usr/local/nginx/html
```

`docker build -t web-server .`

`docker image ls`

`docker container run --name web-server -rm -p 9999:80 web-server:latest`


```
FROM node:4.8
LABEL maintainer="a@b.com"
EXPOSE 8888
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY package.json /usr/src/app
RUN npm install
CMD ["npm", "start"]
VOLUMN /usr/src/app/src/
```

`docker container run --name node-app -rm -p 8888:8888 -v ~/Desktop/abc/src:/usr/src/app/src node-app`

Postgres

```
FROM node:4.8
LABEL maintainer="a@b.com"
EXPOSE 5432
```

`docker container exec -it node-db psql -U postgres`

Postgres Commands

```
\l

\dt

create table votes (id integer primary key, number_of_votes integer, option_name varchar(20));

\dt

insert into votes (id, number_of_votes, option_name) values (1, 0, 'sandwitches');

insert into votes (id, number_of_votes, option_name) values (1, 0, 'tacos');

select * from votes;

```

Show docker networks: `docker network inspect bridge`

