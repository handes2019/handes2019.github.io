---
title: raspberry-docker
date: 2024-10-29 23:05:38
tags: raspberry
category: raspberry
---

#### 安装方法一（脚本安装）

脚本安装是最推荐的方式，只需要输入下面的命令，等待自动安装好即可。

| 1 | `sudo` `curl -sSL https:``//get``.docker.com \| sh` |
| - | ------------------------------------------------------ |

如果采用这一步安装成功，可直接跳到下文的[图形界面](https://so.csdn.net/so/search?q=%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2&spm=1001.2101.3001.7020)安装那里继续阅读。

![](https://i-blog.csdnimg.cn/blog_migrate/119b6052de3d55d7dfbdc35891612a29.png)


安装方法二（apt 安装）
由于 Raspbian 基于 Debian，我们还可以使用 apt 来安装 Docker，首先需要更新一下软件包的索引。

1

sudo apt-get update

安装 HTTPS 所依赖的包

```
sudo apt-get install apt-transport-https

ca-certificates

software-properties-common
```

![](https://i-blog.csdnimg.cn/blog_migrate/714bbdabaae45a4808bbc72ed44d298e.png)

添加 Docker 的 GPG key

```
curl -fsSL https://yum.dockerproject.org/gpg | sudo apt-key add -
```

验证 key id:

```
apt-key fingerprint 58118E89F3A912897C070ADBF76221572C52609D
```

![](https://i-blog.csdnimg.cn/blog_migrate/391d7058187582694a90a8f1e0a7a68e.png)

设置稳定的 repository:

```
sudo add-apt-repository 

"deb https://apt.dockerproject.org/repo/ 

raspbian-$(lsb_release -cs) 

main"
```

注意：如果 add-apt-repository 命令遇到问题，可以尝试将下面这行添加到**树莓派**软件源 sources.list，操作如下：

```
sudo nano /etc/apt/sources.list
```

添加一行：


```
deb https://apt.dockerproject.org/repo/ raspbian-RELEASE main
```

根据自己系统版本调整上面的 RELEASE。通过下面的命令可以查看发行版。

```
lsb_release -cs
```

安装 Docker


```
sudo apt-get update

sudo apt-get -y install docker-engine
```


#### 常用配置和工具命令

```#查看
#查看 Docker 版本
 
docker -v
 
sudo docker pull 仓库/镜像:版本（留空的话默认为 latest）
 
sudo docker run 加参数，用来创建容器
 
#查看运行容器
 
sudo docker ps
 
#查看所有下载的镜像
 
sudo docker images
 
#进入容器终端
 
sudo docker exec -i -t ha /bin/bash
 
#实时查看10行的 ha 日志
 
sudo docker logs -f -t --tail 10 ha
 
#重启 systemctl 守护进程
 
sudo systemctl daemon-reload
 
#设置 Docker 开机启动
 
sudo systemctl enable docker
 
#开启 Docker 服务
 
sudo systemctl start docker
```
