---
title: git相关指令
date: 2023-8-12 19:59:30
category:
tags: git
photos: https://raw.githubusercontent.com/QBrer/blog_img/main/img/202310221552237.png
---

不得不说git的一些命令在多人协作项目时确实重要，这方面的东西的确要抽时间看看，现在用到啥记点啥。

<!-- more -->

github更新后，新仓库master分支改为main分支，使用指令前需要注意一下。

##### 克隆

```
git clone 仓库地址
```

仓库地址分https，ssh与cli三种，自己常用https与ssh，但最近不知道为啥https一直超时，挂vpn也没用。

##### 推送

```
git add .                 //添加工作区内的所有文件到暂存区
git commit –m "提交信息"   //提交，""可不带
git push origin master   //把本地的分支更新到远端origin的master分支上，自己仓库就一个分支，日常直接git push
```

放一张有助于理解的图，只不过这里面的checkout这步没怎么看懂，自己只用它切换过分支。

<img src="https://raw.githubusercontent.com/QBrer/blog_img/main/img/202310221544765.png" style="zoom: 67%;" />



##### 拉取合并

```
git pull origin master   //获取远程分支master并merge到当前分支，同git pull
```

##### 分支相关

```
git branch 分支名	  //创建分支
git checkout 分支名  //切换分支
git branch -d dev	//删除dev分支
git branch	   //查看当前分支，有点鸡肋，现在git窗口上一般在后面会显示当前分支
git merge dev （--no-ff）(-m) //合并，把dev分支的工作成果合并到master分支上
```

##### 代码回退相关

```
git log                  //查看提交历史
git log --pretty=oneline //git log的精简版，只显示commit id，提交历史较多时就很好用
git revert -n commit id  //回退版本，之后commit，push即可
```

