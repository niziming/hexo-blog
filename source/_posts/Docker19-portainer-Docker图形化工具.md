---
title: Docker19-portainer-Docker图形化工具
subtitle: portainer-Docker图形化工具
catalog: true
tags: [Docker,portainer]
date: 2023-12-28 21:37:48
header-img:
---

# Docker19-portainer-Docker图形化工具



## 简介

Portainer 是一款轻量级的应用，它提供了图形化界面，用于方便地管理Docker环境，包括单机环境和集群环境。

1. **拉取并运行 Portainer 2.16.2 容器** 使用以下命令拉取并运行 Portainer 容器：

   ```
   docker volume create portainer_data
   docker run -d -p 8000:8000 -p 9000:9000 --name=portainer \
       --restart=always \
       -v /var/run/docker.sock:/var/run/docker.sock \
       -v portainer_data:/data \
       portainer/portainer-ce:2.16.2
   ```

   这里的 `-v /var/run/docker.sock:/var/run/docker.sock` 选项允许 Portainer 管理 Docker 守护进程。 `-v portainer_data:/data` 用于保存 Portainer 的数据。

2. **访问 Portainer** 打开浏览器，访问 `http://localhost:9000`。你将看到 Portainer 的初始化界面。在这里，你可以创建管理员账户并开始使用 Portainer 来管理 Docker 容器。

3. **（可选）配置防火墙** 如果你在服务器上安装 Portainer，并希望从远程访问它，你需要确保服务器的防火墙允许通过端口 9000 和 8000 的流量。例如，在 Ubuntu 上，你可以使用 UFW 配置防火墙：

   ```
   sudo ufw allow 9000
   sudo ufw allow 8000
   ```

这样就完成了 Portainer 2.16.2 的安装和基本配置。你可以通过 Portainer 的 Web 界面管理你的 Docker 容器和镜像。

重新启动Docker服务：

```
sudo systemctl daemon-reload
sudo systemctl start docker
```



## 引用资料

>
>
>
