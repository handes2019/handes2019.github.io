---
title: 目前国内可用Docker镜像加速器(2025-06)
date: 2025-07-16 00:23:25
tags: Docker
category: Docker
---
<meta name="referrer" content="no-referrer"/>


国内经常使用Docker的朋友，可能都会涉及到配置镜像源的操作，来加速自己的镜像拉取。然而这段时间陆续发现曾经常用的国内镜像站（各种云商和高校镜像站）现在已经不能用了，搜索一番之后，找到可用镜像站或者镜像加速地址，并测试后汇总如下，使用前请自行斟酌。

更新地址可关注：[目前国内可用Docker镜像源汇总](https://link.zhihu.com/?target=https%3A//www.coderjia.cn/archives/dba3f94c-a021-468a-8ac6-e840f85867ea)

## Docker 镜像加速列表（截止到20250603）

> 请注意！有些镜像站仅提供基础镜像或白名单镜像，如果某个加速地址无法拉取到所需的镜像，可以尝试切换到其他地址。有些代理站点是热心网友自费搭建的，请务必合理使用。如果侵犯了您的权益，请随时联系我，我会及时删除相关信息。感谢您的理解与支持！

按照测试脚本进行测试后得到以下能够使用的镜像站：



| [DockerHub](https://zhida.zhihu.com/search?content_id=246729967&content_type=Article&match_order=1&q=DockerHub&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NTI3Njk3NDUsInEiOiJEb2NrZXJIdWIiLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNDY3Mjk5NjcsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.sIvAlXlGlI4m708yjl2aqjB95Ypcdda_opeqDQ8DDfE&zhida_source=entity) 镜像仓库 | 是否正常 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| [http://**docker.m.daocloud.io**](https://link.zhihu.com/?target=http%3A//docker.m.daocloud.io)                                                                                                                                                                                                                                                                                                                                                             | 正常     |
| docker.1ms.run                                                                                                                                                                                                                                                                                                                                                                                                                                              | 正常     |
| [http://**ccr.ccs.tencentyun.com**](https://link.zhihu.com/?target=http%3A//ccr.ccs.tencentyun.com)                                                                                                                                                                                                                                                                                                                                                         | 正常     |
| hub.xdark.top                                                                                                                                                                                                                                                                                                                                                                                                                                               | 正常     |
| hub.fast360.xyz                                                                                                                                                                                                                                                                                                                                                                                                                                             | 正常     |
| docker-0.unsee.tech                                                                                                                                                                                                                                                                                                                                                                                                                                         | 正常     |
| [http://**docker.xuanyuan.me**](https://link.zhihu.com/?target=http%3A//docker.xuanyuan.me)                                                                                                                                                                                                                                                                                                                                                                 | 正常     |
| docker.tbedu.top                                                                                                                                                                                                                                                                                                                                                                                                                                            | 正常     |
| [http://**docker.hlmirror.com**](https://link.zhihu.com/?target=http%3A//docker.hlmirror.com)                                                                                                                                                                                                                                                                                                                                                               | 正常     |
| doublezonline.cloud                                                                                                                                                                                                                                                                                                                                                                                                                                         | 正常     |
| [http://**docker.melikeme.cn**](https://link.zhihu.com/?target=http%3A//docker.melikeme.cn)                                                                                                                                                                                                                                                                                                                                                                 | 正常     |
| image.cloudlayer.icu                                                                                                                                                                                                                                                                                                                                                                                                                                        | 正常     |
| dislabaiot.xyz                                                                                                                                                                                                                                                                                                                                                                                                                                              | 正常     |
| freeno.xyz                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 正常     |
| docker.kejilion.pro                                                                                                                                                                                                                                                                                                                                                                                                                                         | 正常     |

## 配置方式1：临时使用

直接使用，直接拿镜像域名拼接上官方镜像名，例如要拉去镜像`yidadaa/chatgpt-next-web`，可以用下面写法（不要带 `https://`）

```bash
docker pull docker-0.unsee.tech/yidadaa/chatgpt-next-web
```

## 配置方式2：长久有效

> Ubuntu 16.04+、Debian 8+、CentOS 7+

修改文件 `/etc/docker/daemon.json`（如果不存在则需要创建创建，注意不要写入中文），并重启服务。

可直接使用`docker pull`拉去镜像进行测试，或用以下命令检查是否生效：

```bash
docker info
```
