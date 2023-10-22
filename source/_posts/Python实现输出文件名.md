---
title: Python实现批量输出文件名
date: 2023-06-02 16:58:04
category: 编程
tags: Python
photos:
---

设置表情CDN时所用到的批量输出文件名
<!-- more -->
```python
import os
import glob


def list_image_files(folder_path):
    # 首先使用 glob 来获取文件夹下所有的图片文件
    image_files = glob.glob(os.path.join(folder_path, '*.png')) + \
                  glob.glob(os.path.join(folder_path, '*.jpg')) + \

    n=1
    # 输出文件名
    for file in image_files:

        file_name = os.path.basename(file)
        print('"'+"Tieba"+str(n)+'":', '"Tieba/'+file_name+'",')
        n=n+1

# 调用函数并传入文件夹路径
folder_path = 'D:/data/Tieba' 
list_image_files(folder_path)
```

