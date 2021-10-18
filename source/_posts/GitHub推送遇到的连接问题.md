---
title: GitHub推送遇到的连接问题
catalog: true
date: 2021-10-18 14:06:33
subtitle:
header-img:
tags: [github, git]

---

# 遇到的问题

`[ssh: connect to host github.com port 22: Connection refused]`

看问题的秒速应该是连接问题

## 本地生成ssh-key

可以网上搜索相关命令



## 配置config文件

在~/.ssh/下生成此文件

~~~
Host github.com  
User xxxxx@xx.com  	//注册github的邮箱
Hostname ssh.github.com  
PreferredAuthentications publickey  
IdentityFile ~/.ssh/id_rsa  
Port 443
~~~

## 在github上保存公匙

settings > SSH and GPG keys > 保存id_rsa.pub里面的内容

~~~
DELL@DESKTOP-M42R5EL MINGW64 /d/jermaine/IdeaProjects/hexo-blog/source/_posts (master)
$ cd ~

DELL@DESKTOP-M42R5EL MINGW64 ~
$ cd .ssh/

DELL@DESKTOP-M42R5EL MINGW64 ~/.ssh
$ ls
config  id_rsa  id_rsa.pub  known_hosts  known_hosts.old

DELL@DESKTOP-M42R5EL MINGW64 ~/.ssh
$


~~~



## 测试连接github成功

~~~
$ ssh -T git@github.com
Hi niziming! You've successfully authenticated, but GitHub does not provide shell access.
~~~





## 参考资料

> https://www.cnblogs.com/Archer314/p/14641310.html
