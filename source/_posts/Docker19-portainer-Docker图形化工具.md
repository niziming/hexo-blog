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

## 一个portainer管理多个服务器的docker

Portainer 是一个流行的开源 Docker 管理 UI，它允许用户通过一个图形化界面来管理 Docker 容器、镜像、网络和卷。如果你想使用 Portainer 来管理多个服务器上的 Docker，可以按照以下步骤操作：

1. 在一台服务器上安装 Portainer：
   - 拉取 Portainer 镜像：`docker pull portainer/portainer`
   - 运行 Portainer 容器：`docker run -d -p 9000:9000 --name portainer -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer`
   - 访问 Portainer 界面：在浏览器中输入 `http://<服务器IP>:9000` 并设置管理员账号密码。
2. 在其他服务器上配置 Docker 以允许远程管理：
   - 编辑 Docker 服务文件，通常是 `/lib/systemd/system/docker.service`，在 `ExecStart` 行添加 `-H tcp://0.0.0.0:2375` 以开放 Docker API。
   - 重启 Docker 服务：`systemctl daemon-reload && systemctl restart docker`
3. 将其他服务器添加到 Portainer：
   - 在 Portainer 界面中，选择 “Endpoints” -> “Add endpoint”，输入其他服务器的 IP 地址和端口（通常是 2375），并设置权限。
4. 管理 Docker 容器和镜像：
   - 在 Portainer 界面中，你可以查看和管理所有添加的 Docker 服务器上的容器和镜像。

请注意，开放 Docker API 可能会带来安全风险，因此建议在生产环境中使用更安全的方法，如设置 TLS 和使用 Docker Swarm 模式。此外，确保你的服务器防火墙规则限制了对 Portainer 服务的访问权限。

在 Portainer 中，如果你想管理多个独立的 Docker 服务器，你不一定需要在每个服务器上部署一个 Portainer Agent。Portainer 可以直接连接到任何 Docker 守护进程的 API，只要你能够通过网络访问到这些 API。



## Portainer Agent 是一个可选组件

Portainer Agent 是一个可选组件，它提供了一些额外的功能，比如在没有直接访问 Docker 守护进程 API 的情况下管理 Docker 环境。以下是两种常见的管理多个 Docker 服务器的方法：

1. **直接连接到 Docker 守护进程 API**：
   - 你可以通过 Portainer 的 “Endpoints” 功能直接添加每个服务器的 Docker API 端点。
   - 这通常涉及到在每个服务器上开放 Docker API 端口（默认是 2375，但建议更改为其他端口并使用 TLS 加密）。
   - 这种方法不需要在每个服务器上部署额外的 Agent。
2. **使用 Portainer Agent**：
   - Portainer Agent 是一个轻量级的容器，可以部署在每个服务器上。
   - 它作为一个代理，允许 Portainer 通过一个安全的 WebSocket 连接来管理 Docker 环境。
   - 使用 Agent 可以简化配置，特别是在你需要通过防火墙或复杂的网络环境进行管理时。

如果你选择使用 Portainer Agent，你可以在每个服务器上运行以下命令来部署它：

bash

```bash
docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent
```

然后，在 Portainer 的 Web 界面中，你可以通过 “Agents” 部分添加这些 Agent，从而管理这些服务器上的 Docker 环境。

## 引用资料

>
>
>
