---
title: Docker20-docker默认路径修改
subtitle: Docker20-docker默认路径修改
catalog: true
tags: [Docker]
date: 2024-07-21 09:08:59
header-img:
---

# docker 默认路径
Docker 默认使用以下路径来存储不同类型的数据：

1. 镜像存储位置：`/var/lib/docker/image`
2. 容器存储位置：`/var/lib/docker/containers/<container-id>/`
3. 卷存储位置：`/var/lib/docker/volumes/`
4. 配置文件位置：`/etc/docker/daemon.json`

如果需要修改这些默认路径，可以在启动 Docker 服务时通过命令行参数指定新的路径。例如，如果想要将 Docker 的数据存储到不同的分区或磁盘，可以修改 Docker 的服务文件，在启动参数中添加 `-g` 或 `--data-root` 选项来指定新的存储路径。

例如，要将 Docker 的数据存储路径改为 `/new/path/to/docker-data`，可以按照以下步骤操作：

1. 停止 Docker 服务：

   `sudo systemctl stop docker`

   

2. 编辑 Docker 服务文件（例如 `/etc/systemd/system/docker.service`），在 `ExecStart` 参数中添加 `-g` 或 `--data-root` 选项：

   `ExecStart=/usr/bin/dockerd -g /new/path/to/docker-data --containerd=/run/containerd/containerd.sock`

   

3. 重新加载服务配置并启动 Docker 服务：

   `sudo systemctl daemon-reloadsudo systemctl start docker`

   
