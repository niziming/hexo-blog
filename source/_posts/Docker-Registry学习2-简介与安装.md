---
title: Docker-Registry学习2-简介与安装
catalog: true
tags: [Docker]
date: 2019-10-27 10:20:36
subtitle:
header-img:
---
# Docker-Registry学习2-简介与安装
官方的 Docker Hub 是一个用于管理公共镜像的地方，我们可以在上面找到我们想要的镜像，也可以把我们自己的镜像推送上去。但是，有时候我们的服务器无法访问互联网，或者你不希望将自己的镜像放到公网当中，那么你就需要 Docker Registry，它可以用来存储和管理自己的镜像.
~~~
➜  ~ cd /usr/local/
➜  local mkdir docker
➜  local mkdir registry
➜  local cd registry
➜  registry vim docker-compose.yml
~~~

## 配置`docker-compose.yml`
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
~~~
~~~
➜  registry mkdir data
➜  registry chmod 777 data
➜  registry ls
data  docker-compose.yml
➜  registry docker-compose up -d
Creating network "registry_default" with the default driver
Pulling registry (registry:)...
latest: Pulling from library/registry
c87736221ed0: Pull complete
1cc8e0bb44df: Pull complete
54d33bcb37f5: Pull complete
e8afc091c171: Pull complete
b4541f6d3db6: Pull complete
Digest: sha256:8004747f1e8cd820a148fb7499d71a76d45ff66bac6a29129bfdbfdc0154d146
Status: Downloaded newer image for registry:latest
Creating registry ... done
➜  registry docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
registry            latest              f32a97de94e1        7 months ago        25.8MB
hello-world         latest              fce289e99eb9        9 months ago        1.84kB
~~~
安装运行成功
## 查看结果
![](Docker-Registry学习2-简介与安装/1.png)
## 参考资料
> 
