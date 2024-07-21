---
title: Curl指令详解
subtitle: Curl指令
catalog: true
tags: [Linux,curl]
date: 2023-12-28 12:43:28
header-img:
---

# Curl指令详解
curl 是常用的命令行工具，用来请求 Web 服务器。它的名字就是客户端（client）的 URL 工具的意思。

## 简介
它的功能非常强大，命令行参数多达几十种。如果熟练的话，完全可以取代 Postman 这一类的图形界面工具。

如果在一个curl命令中不指定具体的方法，那么默认的就是使用GET方法。对于其它的方法，可以在curl命令中指定：

| method | option |
| ------ | ------ |
| POST   | -d或-F |
| HEAD   | -I     |
| PUT    | -T     |

### 语法：

curl [option] [url]
常见选项：
~~~
-A/--user-agent <string>             设置用户代理发送给服务器
-b/--cookie <name=string/file>    	 cookie字符串或文件读取位置
-c/--cookie-jar <file>               操作结束后把cookie写入到这个文件中
-C/--continue-at <offset>            断点续转
-D/--dump-header <file>              把header信息写入到该文件中
-e/--referer                         来源网址
-f/--fail                            连接失败时不显示http错误
-o/--output                          把输出写到该文件中
-O/--remote-name                     把输出写到该文件中，保留远程文件的文件名
-r/--range <range>                   检索来自HTTP/1.1或FTP服务器字节范围
-s/--silent                          静音模式。不输出任何东西
-T/--upload-file <file>              上传文件
-u/--user <user[:password]>          设置服务器的用户和密码
-w/--write-out [format]              什么输出完成后
-x/--proxy <host[:port]>             在给定的端口上使用HTTP代理
-#/--progress-bar                    进度条显示当前的传送状态

~~~

### Curl支持协议:

> cURL支持的通信协议有：
> FTP、FTPS、HTTP、HTTPS、TFTP、SFTP、Gopher、SCP、Telnet、DICT、FILE、LDAP、LDAPS、IMAP、POP3、SMTP和RTSP。
>
> curl还支持SSL认证、HTTP POST、HTTP PUT、FTP上传,
>
> HTTP form based upload、proxies、HTTP/2、cookies、用户名+密码认证(Basic, Plain, Digest, CRAM-MD5, NTLM,
>
> Negotiate and Kerberos)、file transfer resume、proxy tunneling。



## 如何使用

`curl https://gitee.com/niziming/general_linux_tools/raw/master/install/get-docker.sh`

~~~shell
zm@R7000K:/root$ curl https://gitee.com/niziming/general_linux_tools/raw/master/install/get-docker.sh
#!/bin/sh
set -e
# Docker Engine for Linux installation script.
#
# This script is intended as a convenient way to configure docker's package
# repositories and to install Docker Engine, This script is not recommended
# for production environments. Before running this script, make yourself familiar
# with potential risks and limitations, and refer to the installation manual
# at https://docs.docker.com/engine/install/ for alternative installation methods.
#
# The script:
#
# - Requires `root` or `sudo` privileges to run.
# - Attempts to detect your Linux distribution and version and configure your
#   package management system for you.
# - Doesn't allow you to customize most installation parameters.
# - Installs dependencies and recommendations without asking for confirmation.
# - Installs the latest stable release (by default) of Docker CLI, Docker Engine,
#   Docker Buildx, Docker Compose, containerd, and runc. When using this script
#   to provision a machine, this may result in unexpected major version upgrades
#   of these packages. Always test upgrades in a test environment before
#   deploying to your production systems.
# - Isn't designed to upgrade an existing Docker installation. When using the
#   script to update an existing installation, dependencies may not be updated
#   to the expected version, resulting in outdated versions.
#
# Source code is available at https://github.com/docker/docker-install/
#
# Usage
# ==============================================================================
~~~

#### 保存访问的网页

##### 使用linux的重定向功能保存

`curl URL >> filename.html`

~~~shell
zm@R7000K:/root$ sudo su
[sudo] password for zm:
root@R7000K:~# curl -fsSL https://gitee.com/niziming/general_linux_tools/raw/master/install/get-docker.sh -o get-docker.sh >> /home/get-docker.sh
root@R7000K:~# cd /home/
root@R7000K:/home# ll
total 12
drwxr-xr-x  3 root root 4096 Dec 28 12:48 ./
drwxr-xr-x 19 root root 4096 Dec 28 11:38 ../
-rw-r--r--  1 root root    0 Dec 28 12:48 get-docker.sh
drwxr-x---  2 zm   zm   4096 Dec 28 11:58 zm/

~~~



## 引用资料

>[curl 命令详解_curl命令-CSDN博客](https://blog.csdn.net/Lakers2015/article/details/128627020)
>
>
