---
title: Docker20-docker默认路径修改
subtitle: Docker20-docker默认路径修改
catalog: true
tags: [Docker]
date: 2024-07-21 09:08:59
header-img:
---

# docker 默认路径
### 1. 停止并删除所有容器

```
# 停止所有容器
sudo docker ps -a -q | xargs -r sudo docker stop

# 删除所有容器
sudo docker ps -a -q | xargs -r sudo docker rm
```

`-r`选项确保`xargs`只在有输入时执行命令。

### 2. 删除所有镜像

```
bashCopy code# 删除所有镜像
sudo docker images -q | xargs -r sudo docker rmi -f
```

### 3. 删除所有卷

```
bashCopy code# 删除所有卷
sudo docker volume ls -q | xargs -r sudo docker volume rm
```

### 4. 删除所有网络

```
bashCopy code# 删除所有网络（保留默认网络）
sudo docker network ls | grep -v "bridge\|host\|none" | awk '{if (NR!=1) print $1}' | xargs -r sudo docker network rm
```

### 5. 卸载Docker软件包

根据你的Linux发行版，使用适当的包管理器命令卸载Docker：

#### 对于基于Debian的系统（如Ubuntu）：

```
sudo apt-get purge -y docker-engine docker docker.io docker-ce docker-ce-cli
sudo apt-get autoremove -y --purge docker-engine docker docker.io docker-ce
```

#### 对于基于Red Hat的系统（如CentOS）：

```
bash
Copy code
sudo yum remove docker-ce docker-ce-cli containerd.io
```

#### 对于基于Fedora的系统：

```

sudo dnf remove docker-ce docker-ce-cli containerd.io
```

### 6. 删除Docker相关数据和配置文件

```
sudo rm -rf /var/lib/docker
sudo rm -rf /etc/docker
```

通过这些步骤，你应该能够完全卸载Docker。



### 安装Docker：

```bashCopy code
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
```
方法1：确保Docker守护进程已停止
首先，确保Docker守护进程已完全停止：

sudo systemctl stop docker
sudo pkill -f dockerd

sudo systemctl daemon-reload

sudo systemctl start docker