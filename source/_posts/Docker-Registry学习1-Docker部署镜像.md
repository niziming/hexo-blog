---
title: Docker-Registry学习1-Docker部署镜像
catalog: true
tags: [Docker]
date: 2019-10-27 11:41:33
subtitle:
header-img:
---
# Docker-Registry学习1-Docker部署镜像
## 重新克隆一个虚拟机用于部署
![](Docker-Registry学习1-Docker部署镜像/2.png)
## 修改daemon.json
~~~
➜  ~ vim /etc/docker/daemon.json 
~~~
内容如下:
~~~
{
  "registry-mirrors": ["https://87xm9zvi.mirror.aliyuncs.com"],
  "insecure-registries": ["192.168.115.138:5000"]
}
~~~
重启docker
~~~
➜  ~ systemctl restart docker  
~~~
查看docker信息是否成功
~~~
➜  ~ docker info
Client:
 Debug Mode: false

Server:
 Containers: 1
  Running: 0
  Paused: 0
  Stopped: 1
 Images: 1
 Server Version: 19.03.4
 Storage Driver: overlay2
  Backing Filesystem: extfs
  Supports d_type: true
  Native Overlay Diff: true
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b34a5c8af56e510852c35414db4c1f4fa6172339
 runc version: 3e425f80a8c931f88e6d94a8c831b9d5aa481657
 init version: fec3683
 Security Options:
  apparmor
  seccomp
   Profile: default
 Kernel Version: 4.15.0-66-generic
 Operating System: Ubuntu 18.04.2 LTS
 OSType: linux
 Architecture: x86_64
 CPUs: 2
 Total Memory: 1.924GiB
 Name: ubuntu
 ID: UC5I:QDEG:QVOJ:UKQ7:XC2C:NDC6:UBV3:Y6ZU:JLXZ:O3QJ:NK4C:YWQF
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Registry: https://index.docker.io/v1/
 Labels:
 Experimental: false
 Insecure Registries:
  192.168.115.138:5000
  127.0.0.0/8
 Registry Mirrors:
  https://87xm9zvi.mirror.aliyuncs.com/
 Live Restore Enabled: false
~~~
发现成功
~~~
WARNING: No swap limit support
➜  ~ docker pull tomcat
Using default tag: latest
latest: Pulling from library/tomcat
9a0b0ce99936: Pull complete 
db3b6004c61a: Pull complete 
f8f075920295: Pull complete 
6ef14aff1139: Pull complete 
962785d3b7f9: Pull complete 
631589572f9b: Pull complete 
c55a0c6f4c7b: Pull complete 
379605d88e88: Pull complete 
e056aa10ded8: Pull complete 
6349a1c98d85: Pull complete 
Digest: sha256:77e41dbdf7854f03b9a933510e8852c99d836d42ae85cba4b3bc04e8710dc0f7
Status: Downloaded newer image for tomcat:latest
docker.io/library/tomcat:latest
➜  ~ docker tag tomcat 192.168.115.138:5000/MyTomcat
Error parsing reference: "192.168.115.138:5000/MyTomcat" is not a valid repository/tag: invalid reference format: repository name must be lowercase
➜  ~ docker tag tomcat 192.168.115.138:5000/tomcat
➜  ~ docker push 192.168.115.138:5000/tomcat
The push refers to repository [192.168.115.138:5000/tomcat]
65e5e74a1404: Pushed 
38d8d468142f: Pushed 
08579474bb30: Pushed 
a8902d6047fe: Pushed 
99557920a7c5: Pushed 
7e3c900343d0: Pushed 
b8f8aeff56a8: Pushed 
687890749166: Pushed 
2f77733e9824: Pushed 
97041f29baff: Pushed 
latest: digest: sha256:8aee1001456a722358557b9b1f6ee8eecad675b36e4be10f9238ccd8293bc856 size: 2422
➜  ~ docker images
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
192.168.115.138:5000/tomcat   latest              882487b8be1d        8 days ago          507MB
tomcat                        latest              882487b8be1d        8 days ago          507MB
hello-world                   latest              fce289e99eb9        9 months ago        1.84kB
➜  ~ docker images
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
192.168.115.138:5000/tomcat   latest              882487b8be1d        8 days ago          507MB
tomcat                        latest              882487b8be1d        8 days ago          507MB
hello-world                   latest              fce289e99eb9        9 months ago        1.84kB
~~~
## 查看结果

![](Docker-Registry学习1-Docker部署镜像/1.png)

# 参考资料
>
