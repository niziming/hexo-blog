---
title: Win10安装WSL不依赖微软商店
subtitle: win10安装swl不依赖微软商店
catalog: true
tags: [WSL]
date: 2025-10-23 11:52:37
header-img:
---

# win10安装swl不依赖微软商店



好的，完全没有问题。在 Windows 上安装适用于 Linux 的 Windows 子系统 (WSL) 和 Ubuntu 发行版，完全可以不依赖微软商店。您可以通过命令行（PowerShell 或命令提示符）来完成所有操作，这种方式甚至更受开发者欢迎，因为它更直接、更可控。

以下是详细的步骤，引导您完成整个过程：

### **通过命令行安装 WSL 和 Ubuntu 22.04**

这个过程主要分为两步：首先安装 WSL 核心组件，然后手动下载并安装 Ubuntu。

#### **第 1 步：以管理员身份打开 PowerShell**

这是所有操作的前提。

1. 
2. 点击“开始”按钮。
3. 输入 PowerShell。
4. 在搜索结果中，右键点击“Windows PowerShell”，然后选择“以管理员身份运行”。

#### **第 2 步：启用 WSL 功能**

在 PowerShell 中，您需要运行一个命令来启用 WSL。这个命令会自动处理所有必需的 Windows 功能（如“虚拟机平台”和“适用于 Linux 的 Windows 子系统”）。

- 
- 复制并粘贴以下命令到 PowerShell 窗口，然后按回车： code Powershelldownloadcontent_copyexpand_less`    wsl --install  `
- **注意**：这个命令执行后，通常需要**重启您的计算机**来完成组件的安装。请根据提示操作。

这个命令默认会从微软商店的源头安装最新版本的 Ubuntu。由于您的目标是绕开商店并安装特定版本，我们可以继续下一步。如果该命令自动开始下载 Ubuntu，您可以按 Ctrl + C 终止它，然后执行后续步骤。

#### **第 3 步：手动下载 Ubuntu 22.04.5 LTS**

您需要手动下载 Ubuntu 发行版的 .appx 安装包。幸运的是，微软为此提供了官方的下载链接。

1. 
2. **打开浏览器**，或者您也可以在 PowerShell 中使用 curl 命令来下载。
3. **使用以下链接下载 Ubuntu 22.04.5**：[点击这里直接下载 Ubuntu 22.04.5 LTS 的 .appx 包](https://www.google.com/url?sa=E&q=https%3A%2F%2Faka.ms%2Fwslubuntu2204)如果您想使用 PowerShell 下载（推荐），可以将文件下载到您的“下载”文件夹中。请在 **管理员 PowerShell** 中运行以下命令： code Powershelldownloadcontent_copyexpand_less`    curl.exe -L -o D:\Downloads\Ubuntu-22.04.5.appx https://aka.ms/wslubuntu2204  `*(您可以将 D:\Downloads 替换为您希望保存文件的任何路径)*

#### **第 4 步：手动安装 Ubuntu**

下载完成后，您就可以在指定的路径下找到 Ubuntu-22.04.5.appx 这个文件了。

1. 
2. **导航到文件所在的目录**。如果您将文件下载到了 D:\Downloads，请在 PowerShell 中运行： code Powershelldownloadcontent_copyexpand_less`    cd D:\Downloads  `
3. **运行安装命令**。使用 Add-AppxPackage 命令来安装您刚刚下载的包： code Powershelldownloadcontent_copyexpand_less`    Add-AppxPackage .\Ubuntu-22.04.5.appx  `

安装过程会很快完成。

#### **第 5 步：初始化 Ubuntu**

1. 
2. 安装完成后，点击“开始”菜单，您应该能看到一个新安装的“Ubuntu”应用程序图标。
3. **首次启动 Ubuntu**。点击该图标，会打开一个终端窗口。第一次启动时，系统会提示您“Installing, this may take a few minutes...”。这个过程完成后，您需要为您的 Ubuntu 系统设置一个**用户名**和**密码**。请注意，这个用户名和密码是独立于您的 Windows 账户的，并且输入密码时屏幕上不会显示任何字符。

设置完成后，您就进入了 Ubuntu 的命令行环境。至此，您已成功在不使用微软商店的情况下安装了 Ubuntu 22.04.5 LTS 子系统。

以后，您可以随时通过点击开始菜单的 Ubuntu 图标，或在任何终端（CMD 或 PowerShell）中输入 wsl 或 ubuntu 来启动它。



## 引用资料

>：[点击这里直接下载 Ubuntu 22.04.5 LTS 的 .appx 包](https://www.google.com/url?sa=E&q=https%3A%2F%2Faka.ms%2Fwslubuntu2204)
>
>
