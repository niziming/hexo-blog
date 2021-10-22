---
title: Brook科学上网必备
catalog: true
tags: [梯子, Brook]
date: 2020-12-26 22:16:19
subtitle:
header-img:
---
# 为什么使用Brook

起因是因为在谷歌云平台使用了SSR科学上网后, 一小时不到IP被识别了...

查询相关资料后发现Brook是一个比较偏门的技术, 用这个来科学上网应该比较难被GFW甄别出来

SSR 已经停止更新一段时间了. 相关应该开源已久 GFW团队 也可以针对该技术识别.



# Brook服务搭建前提

- 一台可连接的墙外服务器 推荐GCP
  - 服务器地点可选, IP成服务可以销毁再新建挂载, 相关教程自己去找. 这里不再赘述.

## Brook是什么

官方github介绍

> Brook is a cross-platform strong encryption and not detectable proxy.
> Brook's goal is to keep it **simple**, **stupid** and **not detectable**.

跨平台 强加密 无法被检测

## Brook使用

### 命令行安装 brook



### 下载Brook

命令: `$ curl -L https://github.com/txthinking/brook/releases/download/v20200909/brook_linux_amd64 -o /usr/bin/brook $ chmod +x /usr/bin/brook`

```
☁  jermainenee  curl -L https://github.com/txthinking/brook/releases/download/v20210101/brook_linux_amd64 -o /usr/b
in/brook
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   641  100   641    0     0    981      0 --:--:-- --:--:-- --:--:--   981
100 10.8M  100 10.8M    0     0  3062k      0  0:00:03  0:00:03 --:--:-- 5206k
☁  jermainenee  chmod +x /usr/bin/brook

```

### 安装 nami

应该是一个包管理器, 官方推荐使用nami安装

命令:`$ curl -L https://git.io/getnami | bash && sleep 6 && exec -l $SHELL`

```
☁  jermainenee  nami install github.com/txthinking/brook
zsh: command not found: nami
☁  jermainenee  curl -L https://git.io/getnami | bash && sleep 6 && exec -l $SHELL
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
100  1478  100  1478    0     0    946      0  0:00:01  0:00:01 --:--:--   946
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   642  100   642    0     0    992      0 --:--:-- --:--:-- --:--:--   990
100 11.5M  100 11.5M    0     0  3183k      0  0:00:03  0:00:03 --:--:-- 5304k
+-------------------+----------------------------+
| Package           | github.com/txthinking/nami |
|                   |                            |
| Installed Version | v20201101                  |
| Installed Files   | nami                       |
+-------------------+----------------------------+

☁  jermainenee  nami install github.com/txthinking/nami
+-------------------+----------------------------+
| Package           | github.com/txthinking/nami |
|                   |                            |
| Installed Version | v20201101                  |
| Installed Files   | nami                       |
+-------------------+----------------------------+

```

### 安装brook

命令: `$ nami install github.com/txthinking/brook`

```
☁  jermainenee  nami install github.com/txthinking/brook
+-------------------+-----------------------------+
| Package           | github.com/txthinking/brook |
|                   |                             |
| Installed Version | v20210101                   |
| Installed Files   | brook                       |
+-------------------+-----------------------------+

```



### Brook的使用

命令: `brook server -l :9999 -p hello`

:9999 是端口暴露

-p hello 是密码

```
☁  jermainenee  brook server -l :8004 -p hello
^C2020/12/26 21:43:47 main.go:928: accept tcp [::]:8004: use of closed network connection

```

测试连接

![QQ截图20201226223304](Brook科学上网必备/QQ截图20201226223304.png)

网速测试

![微信图片_20201226221856](Brook科学上网必备/微信图片_20201226221856.png)

这里一旦关掉terminal的话brook服务就会停止, 所以按照官方文档开启守护进程

### 安装joker 开启守护进程



```
☁  jermainenee  nami install github.com/txthinking/joker
+-------------------+-----------------------------+
| Package           | github.com/txthinking/joker |
|                   |                             |
| Installed Version | v20200902                   |
| Installed Files   | joker                       |
+-------------------+-----------------------------+

```

### 配置brook

```
☁  jermainenee  joker brook server -l :8004 -p ziming
☁  jermainenee  joker list
17298 pts/0    Sl     0:00 brook server -l :8004 -p ziming
☁  jermainenee  
☁  jermainenee  ./shadowsocks-all.sh uninstall
Which Shadowsocks server you want to uninstall?
1) Shadowsocks-Python
2) ShadowsocksR
3) Shadowsocks-Go
4) Shadowsocks-libev
Please enter a number [1-4]:2

You choose = ShadowsocksR

Are you sure uninstall ShadowsocksR? [y/n]
(default: n):y
IPv6 support
2020-12-26 21:45:02 INFO     shell.py:74 ShadowsocksR SSRR 3.2.2 2018-05-22
stopped
Stopping ShadowsocksR success
[Info] ShadowsocksR uninstall success
```

### windows client Brook客户端下载

> 下载地址
>
> https://github.com/txthinking/brook/releases

### IOS 移动端 下载

> https://apps.apple.com/us/app/brook-undetectable-proxy-vpn/id1216002642

目前还是免费的,而且是官方开发的app

![](Brook科学上网必备/IMG_4987.PNG)

### 总结

brook 的配置十分简单, 使用起来比ssr服务还要简单.

brook 总共4总协议, 新的协议名称为server,这里采用server协议

![QQ截图20201226223632](Brook科学上网必备/QQ截图20201226223632.png)

打开YouTube

![QQ截图20201226223743](Brook科学上网必备/QQ截图20201226223743.png)



## 参考资料
> https://txthinking.github.io/brook/#/
>
> https://github.com/txthinking/brook
