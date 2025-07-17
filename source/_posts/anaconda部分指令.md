---
title: anaconda部分指令
date: 2022-12-08 21:17:16
category:
tags: Python
photos:
---
anaconda在装包过程会用到的部分指令
<!-- more -->
1.设置默认镜像

```
pip config set global.index-url http://pypi.douban.com/simple
```

2.anaconda

```
conda env list                      #显示所有的虚拟环境
conda activate myenv                #开启myenv环境
conda deactivate                    #关闭环境
conda install 包名=版本
pip install -i https://mirrors.aliyun.com/pypi/simple/ 包名
```

3.常用国内镜像

```
阿里云 http://mirrors.aliyun.com/pypi/simple/

中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/

豆瓣(douban) http://pypi.douban.com/simple/

清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/

中国科学技术大学 http://pypi.mirrors.ustc.edu.cn/simple/
```

