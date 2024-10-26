---
title: 莓派学习
date: 2024-10-26 10:50:12
tags: raspberry
category: raspberry
---

Error 1: Partition does not have a FAT file system
        硬件方面使用的是树莓派4B，RAM=4G，tf卡用的是闪迪64G。

    系统方面使用的是Ubuntu 桌面 22.04.3 LTS（arm64）

    注：在第一次安装的时候一定要注意自己安装的系统是arm64的还是armhf，这在后面的wiringpi库安装会很有用。（当时因为没有注意这个问题导致在安装wiringpi上面消耗了很多时间）ubuntu下载地址：
在树莓派上安装Ubuntu | Ubuntu
https://cn.ubuntu.com/download/raspberry-pi

下载完成后你将会得到：这个时候我们就完成了系统的下载。接下来我们需要准备一个TF卡，使用烧录软件将系统文件烧录入tf卡中。

烧录软件链接：
Raspberry Pi OS – Raspberry Pi
https://www.raspberrypi.com/software/

问题一：第一次烧录的时候，出现了提示Partition does not have a FAT file system.

问题分析：

    这个问题产生原因是镜像文件出现问题。建议检查镜像文件是否为树莓派使用的Ubuntu镜像文件（是否下载成光盘映像文件）

错误文件长这样：

解决方案：使用烧录软件中的清除SD卡，将错误系统删除，重新烧录正确的系统镜像

注：这里需要注意，sd卡插入电脑后在文件管理器中是无法识别的，如果需要格式化磁盘会提示有写保护，这里不要慌，直接用烧录软件里的清楚SD卡即可。

Error2：系统init
SSH远程登陆对于没有显示屏的小伙伴来说是非常有效远程控制树莓派的好东西。

如果要实现SSH远程控制，则需要使电脑和树莓派在同一个局域网下（可以电脑开个热点啦）

电脑软件需求：xshell

在我做SSH远程控制之前，翻阅了很多别的大佬的文章，大径相同的解决方案就是在sd卡中加入两个文件，但是我经过好几次尝试，依旧很难将树莓派连接到我电脑的热点上，后来借用同学的显示屏才找到问题。

这里插入一下一个大佬的文档，内部有xshell的教程大家可以参考一下：

【树莓派】保姆级教程，如何优雅的使用ssh连接树莓派_树莓派ssh_Yuki i i i i i i i的博客-CSDN博客
https://blog.csdn.net/u014576547/article/details/123495010
言归正传：在接入显示器后，发现系统还没完成初始化，需要等待5min左右让系统完成初始化。初始化过程中就可以完成wifi连入电脑局域网，初始化期间需要注意保持电脑网络通畅。

完成系统初始化后，可以通过电脑的热点查看树莓派的地址，根据上面文档的教程完成xshell的配置。

Error3：xshell报port 22错误
在完成找到查找到树莓派ip地址后，xshell依旧无法远程登陆树莓派，提示port 22错误。

该问题应该是 新的系统没有安装ssh端or没有打开ssh导致的，我最后参考了一个大佬的文档解决该问题，参考文档如下：

解决Xshell连接服务器失败：Could not connect to ‘192.168.191.128‘ (port 22): Connection failed._何极光的博客-CSDN博客
https://luckylifes.blog.csdn.net/article/details/107796879
根据上面的步骤进行调试，即可完成xshell和树莓派的连接

Suggest：关于获得root权限
因为我用的是C语言编写gpio，需要获得系统root超级权限，获得root权限方法可见以下文件：

Raspberry pi 获取root权限_树莓派 提权_flyingool的博客-CSDN博客
https://blog.csdn.net/linuxpassion/article/details/53972003

Error4：wiringpi安装
如果想要使用C语言编写树莓派，需要wiringpi的库。

在安装wiringpi之前，如果您是和我一样安装Ubuntu（arm64）系统的，可以参考我的操作，如果您是安装了树莓派官方系统或者32位操作系统，参考一下文档（一定要确定您装的系统64位还是32位）：

树莓派4B-WiringPi库的安装和使用 (C和Python版)_树莓派4b安装wiringpi_电子芯吧客的博客-CSDN博客
https://blog.csdn.net/ICXBK/article/details/108461743
如果是arm64的系统，推荐从github安装：

sudo apt-get install git //安装git
sudo apt upset //回车
sudo apt upgrade //回车
sudo apt-get install build//回车
git clone https://github.com/WiringPi/WiringPi.git//建议流量下载，回车
cd WiringPi//回车
./build//安装
gpio -v //回车
gpio readall //回车
完成后界面如下：

注：4B的wiringpi的版本必须要高于2.52，否则执行不了gpio readall。

suggest：最后编译.c文件的时候，可以使用：

gcc xxx.c -lwiringPi
以上是树莓派在ubuntu(arm64)系统部署，ssh，wiringpi时遇到的问题，个人解决查询的资料和个人的最终解决方案，解决方案亲测有效，最后成功成为点灯大师。
