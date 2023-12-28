---
title: Docker-Registry学习3-配置WebUI与客户端
catalog: true
tags: [Docker]
date: 2019-10-27 11:49:21
subtitle:
header-img:
---
# Docker-Registry学习3-配置WebUI与客户端 
## 停止并删除原来的registry
docker docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
a9d6cba04f16        registry            "/entrypoint.sh /etc…"   2 hours ago         Up About an hour    0.0.0.0:5000->5000/tcp   registry
➜  docker docker stop a9
a9
➜  docker docker rm a9
a9
➜  docker vim registry/docker-compose.yml
➜  docker cd registry
➜  registry ls
data
➜  registry vim docker-compose.yml

## 配置docker-registry-frontend
我们使用 docker-compose 来安装和运行，docker-compose.yml 配置如下
~~~
version: '3.1'
services:
  registry:
    image: registry
    restart: always
    container_name: registry
    ports:
      - 5000:5000
    volumes:
      - /usr/local/docker/registry/data:/var/lib/registry
  frontend:
    image: konradkleine/docker-registry-frontend:v2
    ports:
      - 8080:80
    volumes:
      - ./certs/frontend.crt:/etc/apache2/server.crt:ro
      - ./certs/frontend.key:/etc/apache2/server.key:ro
    environment:
      - ENV_DOCKER_REGISTRY_HOST=192.168.75.133
      - ENV_DOCKER_REGISTRY_PORT=5000
~~~
## 启动容器
~~~
➜  registry docker-compose up -d
Pulling frontend (konradkleine/docker-registry-frontend:v2)...
v2: Pulling from konradkleine/docker-registry-frontend
85b1f47fba49: Pulling fs layer
e3c64813de17: Pulling fs layer
6e61107884ac: Pulling fs layer
411f14e0e0fd: Waiting
987d1071cd71: Waiting
95913db6ef30: Waiting
1eb7ee3fbde2: Pull complete
9b6f26b1b1a1: Pull complete
daa6941a3108: Pull complete
86cc842193a6: Pull complete
024ab6890532: Pull complete
af9b7d0cb338: Pull complete
02f33fb0dcad: Pull complete
e8275670ee05: Pull complete
1c1a56903b01: Pull complete
afc4e94602b9: Pull complete
df1a95efa681: Pull complete
d8bcb7be9e08: Pull complete
d9c69b7bcc4f: Pull complete
2a14b209069e: Pull complete
e7c2bcdf63d5: Pull complete
efc16e6bbbea: Pull complete
552460069ca8: Pull complete
e6b075740da3: Pull complete
9976bc800046: Pull complete
Digest: sha256:181aad54ee64312a57f8ccba5247c67358de18886d5e2f383b8c4b80a7a5edf6
Status: Downloaded newer image for konradkleine/docker-registry-frontend:v2
Creating registry_frontend_1 ... done
Creating registry            ... done
~~~

## 查看结果
![](Docker-Registry学习3-配置WebUI与客户端/1.png)
![](Docker-Registry学习3-配置WebUI与客户端/2.png)
![](Docker-Registry学习3-配置WebUI与客户端/3.png)
![](Docker-Registry学习3-配置WebUI与客户端/4.png)

## 参考资料
> 
