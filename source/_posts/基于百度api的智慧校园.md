---
title: 基于百度api的智慧校园
date: 2023-12-27 17:26:32
category: 前端
tags: vue
photos:
---

<!-- more -->

压图压得有点厉害啊

#### 1 系统设计

##### **1.1**系统架构

（1）数据层：主要为MySQL数据库及JSON文件，其中MySQL数据库用于存放校园各建筑，充电桩及消防栓地理位置及名称等信息，JSON文件则用于存储人流量模拟数据。

（2）应用支撑层：同二课程设计题目和内容中课程设计内容，故不赘述。

（3）业务逻辑层：包括基本信息查询、人流量分析、充电桩信息，消防保障四大模块。

（4）表现层：支持各大主流浏览器。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271720075.jpg)

图 1 系统架构图

##### **1.2**功能架构

本课程设计包含基本信息查询、人流量分析、充电桩信息，消防保障四大功能，具体功能描述如下：

（1）基本信息查询：用户在地图上点击感兴趣或想要查询的建筑物后，系统将会显示出该建筑物的名称，基本信息及实景图片。用户可在搜索框中输入起点和终点，选择好起点和终点后会自动规划路径，并可以在路径规划栏中或通过单击图中的路径显示路径信息和导航信息。

（2）人流量分析：通过对人群所在位置信息进行核密度分析，通过热力图与热力网格模型来直观表示，使用户对全校各处人流量具有更加清楚的认知。

（3）充电桩信息：点击想要查询的充电桩可以显示出该充电桩的编号及该充电桩充电剩余时间，并且可以通过显示充电桩来获取充电桩的分布情况。

（4）消防保障：用户可以在目击火灾发生时在该系统提交火灾发生地，通过右击地图上的任意位置点击上传火灾地点，系统会自动显示所设置的缓冲区半径范围内的消防栓，双击指定消防栓可以出现导航信息，使专业人员能够尽快采取行动，控制解决火灾。

#### **2**系统开发

##### **2.1**环境搭建

（1）创建Vue项目

①安装node.js，前往node.js官网下载长期维护版

②全局安装vue-cli，打开命令行输入npm install -g @vue/cli

③创建Vue项目，命令行输入vue create 项目名称，该项目为vue2项目，故配置选择vue2，其他配置默认。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271721676.jpg)

图 2 项目目录

（2）安装Flask

①在项目src目录下创建flask_vue文件夹，作为与后端文件交互文件夹。

②在命令行中进入自己python的虚拟环境下，输入pip install flask安装Flask框架。

（3）调用百度API及其下的MapVGL库

①获取百度服务密钥（AK）。

②调用百度API及MapVGL库，于public/index.html目录下添加。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271720429.jpg)

图 3 调用百度API

##### **2.2**路由设置

（1）新建src/route/route.js

定义路由数组，内容如下

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271721990.jpg)

图 4 route.js

（2）NavButton.vue 

设置导航栏，点击链接调用goTo方法，将路由切换到对应path。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271721136.jpg)

图 5 导航栏goTo跳转

（3）goTo方法定义

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722149.jpg)

图 6 goTo方法定义

##### **2.3**功能实现

（1）百度地图的调用

①初始化地图，确定中心点，放大层别与地图样式。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722088.jpg)

图 7 初始化地图

②添加3D，放大缩小，定位控件，并设置位置。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722099.jpg)

图 8 添加控件

③结果呈现

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722072.jpg)

图 9 百度地图呈现结果

（2）路径规划

①页面呈现

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722568.jpg)

图 10 路径规划页面呈现部分代码

②功能实现，调用百度的路径规划

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722556.jpg)

图 11 路径规划功能实现

③结果呈现

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722100.jpg)

图 12 路径规划呈现结果

（3）人流量分析热力图与热力网格

①数据导入，本项目使用自设场景数据来模拟相应场景，数据格式为JSON格式，通过axios导入。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722988.jpg)

图 13 数据加载方法定义

②定义热力图图层，设置大小，最大值及渐变色。

![](https://raw.githubusercontent.com/QBrer/blog_img/main/img/202403171737484.jpg)

图 14 热力图

③定义热力网格图层，设置显示大小，最高高度，最低高度，渐变色等配置。

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722552.jpg)

图 15 热力网格

④结果呈现

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722682.jpg)

图 16 热力图及热力网格呈现

（4）通过Flask调用Python文件进行数字识别

①Vue组件部分

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722473.jpg)

图 17 vue组件部分代码

②serve.py

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722087.jpg)

图 18 serve.py代码

（5）消防保障缓冲区分析

①添加右键菜单上传火灾地点

![img](file:///C:/Users/QBrer/AppData/Local/Temp/msohtmlclip1/01/clip_image038.jpg)

图 19 右键菜单

②添加扩散圆图层，设置动画持续时间和动画步数

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271722759.jpg)

图 20 扩散圆图层

③判断扩散圆半径内是否有消防栓，如果有，添加标记，可双击进行路线规划

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271723012.jpg)

图 21 判断范围内是否有可用的消防栓

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271723266.jpg)

图 22 导航到可用的消防栓

④结果呈现

![img](https://raw.githubusercontent.com/QBrer/blog_img/main/202402271723261.jpg)

图 23 缓冲区分析结果呈现

 