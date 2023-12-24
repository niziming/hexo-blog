---
title: PEV7.2_all_in_one_虚拟机大全_02_pve安装windows10镜像
subtitle: PEV7.2_all_in_one_虚拟机大全_02_pve安装windows10镜像
catalog: true
tags: []
date: 2023-04-02 09:31:30
header-img:
---

# pve安装windows10镜像



## 简介

第一章我们下载了windows 精简版, 这里将使用pve安装win10精简版

## 准备工作

- 下载win10 安装镜像
- 将镜像上传至pve
- 挂载硬盘
  - **7.0以后版本有可视化界面可以操作挂载非常方便**
  - 这里将挂载另外一块磁盘
- windows 驱动 Windows VirtIO https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso 
  - 下载完成后上传到Samsung
  - ![image-20230402111711356](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402111711356.png)


## 开始

### 选择三星这块磁盘镜像擦除

![image-20230402094806454](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402094806454.png)

- 销毁

![image-20230402095123220](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095123220.png)

![image-20230402095141712](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095141712.png)

- 创建 目录

  ![image-20230402095216800](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095216800.png)

  ![image-20230402095301548](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095301548.png)

  ![image-20230402095309659](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095309659.png)

  目录就创建完成了

  ![image-20230402095325044](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095325044.png)

### 上传镜像

![image-20230402095429545](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095429545.png)

![image-20230402095435474](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095435474.png)

精简版win10仅有1.5GB

![image-20230402095449287](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095449287.png)

![image-20230402095454853](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402095454853.png)



### 添加一台虚拟机

![image-20230402101728476](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402101728476.png)

![image-20230402101735310](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402101735310.png)



选择刚才上传的IOS镜像

![image-20230402101835330](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402101835330-1680401916355-1.png)



系统

![image-20230402105823150](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402105823150.png)

磁盘

![image-20230402105811426](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402105811426.png)

CPU

![image-20230402105926387](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402105926387.png)

内存 16GB

![image-20230402110027055](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402110027055.png)

网络

![image-20230402110125721](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402110125721-1680404486706-3.png)

点击下一步确认![image-20230402110202116](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402110202116.png)



根据个人需求 重新挂载了几个硬盘上去

![image-20230402111942143](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402111942143.png)

在ISO镜像这儿选择刚刚下载的 Windows VirtIO Drivers 镜像文件

![image-20230402111955701](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402111955701.png)

添加完成后我们则可以看到会有两个 CD/DVD驱动器，一个是我们的win10镜像文件，还有一个则是驱动的镜像文件

![image-20230402112111415](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112111415.png)

安装 win10
我们选中创建的虚拟机，点击控制台菜单，然后点击启动，开启虚拟机

![image-20230402112101262](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112101262.png)

![image-20230402112132449](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112132449.png)

点击下一步

![image-20230402112220226](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112220226.png)



选择我们要安装的版本，然后点击下一步

![image-20230402112257070](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112257070.png)

我想将80GB的作为系统盘,所以选择了驱动器0开始分配磁盘

点击下一步开始安装

![image-20230402112501324](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112501324.png)

等待它自动重启即可

现在我们等待它加载完成，并完成相应的设置

![image-20230402112645414](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112645414.png)

按照自己需求一步一步设置

![image-20230402112830287](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402112830287.png)

设置完成后进入桌面

![image-20230402113010413](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402113010413.png)

![image-20230402113218792](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402113218792.png)

可以看到精简版按照后系统盘大小14gb

![image-20230402113335134](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402113335134.png)

然后按照自己需求配置下windows初始设置



### 驱动安装及网络设置

![image-20230402114936293](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402114936293.png)

![image-20230402115019200](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115019200.png)

点击下一步安装![image-20230402115032574](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115032574.png)

网络通了

![image-20230402115053451](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115053451.png)

![image-20230402115126766](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115126766.png)

![image-20230402115136816](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115136816.png)

安装个edge 如果商店无法下载 可以上浏览器下载安装

![image-20230402115223414](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115223414.png)



![image-20230402115331900](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115331900.png)

![image-20230402115451807](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402115451807.png)



### 启动引导切换,移除cd/dvd驱动

移除cd/dvd驱动

![image-20230402120922825](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402120922825.png)



启动引导改为C盘启动![image-20230402120939152](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402120939152.png)

### 备份![image-20230402121001708](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402121001708.png)



下章将探索如何实现硬件直通及独立显示器和鼠标键盘



### 转换模板

![image-20230402121310429](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402121310429.png)



### 克隆

![image-20230402121331706](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402121331706.png)

![image-20230402121357074](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402121357074.png)

### 安装远程桌面

启动虚拟机

![image-20230402121414378](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402121414378.png)

![image-20230402121432388](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402121432388.png)

下载安装 todesk

![image-20230402121819905](PEV7-2-all-in-one-虚拟机大全-03-pve安装windows10镜像/image-20230402121819905.png)

这样就算人没在家也可以控制那台虚拟机了





## 引用资料

>[PVE 安装 windows10 - 哔哩哔哩 (bilibili.com)](https://www.bilibili.com/read/cv18974318)
>
>
