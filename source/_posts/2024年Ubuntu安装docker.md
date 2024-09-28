---
title: 2024年Ubuntu安装docker
subtitle: 2024年Ubuntu安装docker
catalog: true
tags: [docker]
date: 2024-09-28 11:24:47
header-img:
---

# Ubuntu安装docker



在Ubuntu系统上安装Docker，你可以按照以下步骤进行：

1. **更新系统包索引**：
   打开终端，首先更新你的包索引：
   ```bash
   sudo apt update
   ```

2. **安装依赖包**：
   安装一些必要的依赖包：
   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```

3. **添加Docker的官方GPG密钥**：
   添加Docker的官方GPG密钥到你的系统中：
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

4. **添加Docker的官方APT仓库**：
   添加Docker的官方APT仓库到你的系统中：
   ```bash
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   ```

5. **再次更新系统包索引**：
   添加了新的APT仓库后，再次更新包索引：
   ```bash
   sudo apt update
   ```

6. **安装Docker CE**：
   安装Docker CE（社区版）：
   ```bash
   sudo apt install docker-ce
   ```

7. **验证Docker是否安装成功**：
   安装完成后，运行以下命令来验证Docker是否安装成功：
   ```bash
   sudo docker run hello-world
   ```
   如果一切正常，你将看到一条消息，表明Docker容器正在运行。

8. **添加用户到docker组**（可选）：
   默认情况下，`docker`命令会使用`root`权限。为了避免每次使用`docker`命令时都需要`sudo`，你可以将你的用户添加到`docker`组：
   ```bash
   sudo usermod -aG docker $USER
   ```
   添加用户到`docker`组后，你需要注销并重新登录，或者重启系统，才能使更改生效。

9. **安装Docker Compose**（可选）：
   Docker Compose是一个用于定义和运行多容器Docker应用程序的工具。你可以使用以下命令安装：
   ```bash
   curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   sudo chmod +x /usr/local/bin/docker-compose
   ```
   请确保替换上面的URL中的版本号为最新的版本。

10. **验证Docker Compose是否安装成功**：
    安装完成后，运行以下命令来验证Docker Compose是否安装成功：
    ```bash
    docker-compose --version
    ```

现在，Docker已经安装在你的Ubuntu系统上了，你可以开始创建和运行容器了。



## 引用资料

>
>
>
