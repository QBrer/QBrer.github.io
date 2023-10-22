---
title: hexo多设备同步更新
date: 2023-10-12 22:32:40
category:
tags: git
photos:
---
写博客这件事情老是坚持不下来，一方面确实是懒，还有很大一方面是两个设备轮流着用，hexo又是个纯静态框架，导致自己老是在一个设备写好.md文件，传到另一个设备再部署，实在是麻烦，最近抽时间总算是解决了这个问题，写博客也顺手了很多。
<!-- more -->

#### 解决原理

该方法主要利用git与分支管理。通过hexo d部署的静态文件会部署在全局配置文件中所写的分支上，默认是master分支，而通过git clone与git pull所拉取的源文件分支为github仓库所设置的默认分支，通过两个分支分别处理就可以解决多个设备的同步问题。

#### 方法步骤

##### 1.有源文件的老设备

①在自己博客仓库新创建hexo分支，并将其改为默认分支

<img src="https://raw.githubusercontent.com/QBrer/blog_img/main/img/202310132118356.png" style="zoom: 50%;" />

②通过git clone将hexo分支文件下载到本地（此时该分支文件与master分支相同），仅留下.git文件，其余文件全部删除，并将自己原本的博客源文件中除.deploy_git 以外的文件都复制到该文件夹（这个步骤是为了更新部署的分支，使推送与拉取分支变为新创建的hexo分支）

③开始推送

```
git add . 

git commit –m add_branch 

git push
```

##### 2.无源文件的新设备

①添加新设备的ssh key到github账户

![](https://raw.githubusercontent.com/QBrer/blog_img/main/img/202310162013087.png)

②克隆hexo分支下源文件到本地

③安装所需要的依赖

```
npm install hexo

npm install

npm install hexo-deployer-git
```

④修改编写博客

⑤部署到页面上

```
hexo clean

hexo g

hexo d
```

⑤推送

```
git add . 

git commit –m add_branch 

git push
```

##### 3.换设备编写时

①git pull合并更新

②修改编写博客并部署到页面上

③推送

