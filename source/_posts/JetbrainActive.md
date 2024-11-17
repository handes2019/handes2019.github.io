---
title: Jetbrains全家桶激活方法
date: 2024-11-17 11:34:39
tags: Jetbrain
category: Jetbrain
---
<meta name="referrer" content="no-referrer"/>


亲测有效，此处以phpstrom为例，按理其他产品也可以用相同的方式激活。

原理是我们通过代码搜索其他授权服务器进行永久激活。

方式一   通过censys

https://search.censys.io/

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155249391-1953065875.png)

用到的代码：

services.http.response.headers.location: account.jetbrains.com/fls-auth

我们将上面这串代码services.http.response.headers.location: account.jetbrains.com/fls-auth复制进censys搜索框中进行搜索，会出现：

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155302597-1592053156.png)

 可以看到出现了很多对应跳转到 jetbrains 的服务器IP和网址,我们随便点击一个看下状态是不是 302 只有 302 的才能正常使用 。

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155318305-1629682908.png)

 然后我们复制域名或者IP到jetbrains全家桶进行激活,比如我们使用第一个 49.234.70.205 复制到 License server 。

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155330923-1959395538.png)

可以看到已经连接到jetbrains授权服务器成功了,然后我们点击 ACTIVATE 进行启动就可以了。

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155344212-1484480805.png)

方式二 通过shodan

https://www.shodan.io

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155355123-66450133.png)

用到的代码：

Location: https://account.jetbrains.com/fls-auth

和方式一同样我们将代码复制到搜索框进行搜索就可以了。

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155414065-1828167293.png)

 通过shodan我们可以直接看到 HTTP/1.1 302 不用再每个都要点进去看了,相对来说比方式一方便。

![](https://img2023.cnblogs.com/blog/1869035/202302/1869035-20230224155428301-1587772253.png)

激活使用jetbrains全家桶方式和censys一样,激活之后我们可以看到用的是 天津理工大学 的 jetbrains授权服务器 。

jetbrains激活原理

通过以上方式激活 jetbrains全家桶 主要是用到了爬取网站服务这一类的搜索引擎实现的。通过搜索引擎我们找到全世界的 jetbrains授权服务器进行激活。

注意事项

每个服务器IP承载激活的数量优先, 如果激活时候提示失败,可以多换几个.

本文章仅用于学习研究勿用于非法.

请支持正版
