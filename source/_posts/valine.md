---
title: Valine国内节点无法显示评论
date: 2023-08-18 17:04:02
category: 服务器
tags: [Valine, LeanCloud]
photos: 
---

自己原先已经解决了这个问题，最近换了一个域名之后却忘了原先是怎么解决的了，导致又浪费了好长时间去找解决办法，现在记录下来，免得到时候又要一篇篇博客的找配置方法。
<!-- more -->
### 原因
valine作为一个完全纯前端的评论插件，通过leancloud来实现评论功能，而国际版的leancloud共享域名不再向中国大陆提供服务，这导致国内节点无法使用评论功能
<img src="/someimg/8311.jpg" style="zoom: 50%;" />

### 解决方法
官方已给出了解决方法，就是绑定上自己的域名或者使用leancloud国内版（需要实名认证），感觉还是绑定域名稍微快点。

进入leancloud国际版，设置-域名绑定-绑定新域名。官方这里是绑定二级域名,但不知道为啥我绑定之后没用，国内依旧无法使用评论，后来看csdn上一篇博客说要绑定三级域名，绑完确实可以用了，不是很懂。按照leancloud所给推荐配置域名解析：

<img src="/someimg/Snipaste_2023-08-31_16-27-11.png" alt="1" style="zoom:80%;" />

<img src="/someimg/Snipaste_2023-08-31_18-05-07.png" alt="8312" style="zoom:80%;" />

最后，进入自己博客主题配置文件更改valine的serverURLs即可。

