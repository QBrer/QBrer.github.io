---
title: vue+远程mysql数据库实现简单的增删改查
date: 2023-10-11 19:48:23
category: 前端
tags: [vue, mysql]
photos:
---

实现前后端分离，读取远程服务器上的数据并进行读取显示

<!-- more -->

项目目录如下：

<img src="https://raw.githubusercontent.com/QBrer/blog_img/main/img/202407272134577.png" style="zoom:50%;" />

#### 1.数据库部分

数据库已在服务器中建立好，打开相应的权限，连接即可

在db文件夹下的index.js中设置数据库地址：

<img src="https://raw.githubusercontent.com/QBrer/blog_img/main/img/202407272137437.png" style="zoom:50%;" />

在api文件夹下的list.js写入对应的sql语句：

<img src="https://raw.githubusercontent.com/QBrer/blog_img/main/img/202407272138908.png" style="zoom: 33%;" />

最后设置好路由与跨域部分

#### 2.前端部分

简单写一下对应的按钮与交互逻辑

<img src="https://raw.githubusercontent.com/QBrer/blog_img/main/img/202407272142726.png" style="zoom:33%;" />

<img src="https://raw.githubusercontent.com/QBrer/blog_img/main/img/202407272143420.png" style="zoom: 33%;" />

#### 3.运行项目

直接执行npm run serve，node index，即可调用远程数据库中的数据并进行增删改查。

