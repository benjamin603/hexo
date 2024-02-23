---
title: 图床管理工具Piclist推荐
abbrlink: 49685
date: 2024-02-17 23:11:27
categories: 折腾记录
tags: Piclist
index_img: https://r2.snbing.com/img/cover/0269585bb565e997.webp
sticky:
comment:
---

PicList是一款高效的云存储和图床平台管理工具，在PicGo的基础上经过深度的二次开发，不仅完整保留了PicGo的所有功能，还增添了许多新的feature。例如相册支持同步云端删除文件，内置图床额外添加了WebDav、本地图床和SFTP等。PicList同时增加了完整的云存储管理功能，包括云端目录查看、文件搜索、批量上传下载和删除文件，复制多种格式文件链接和图片/markdown/文本/视频预览等，另外还有更加强大的相册和多项功能新增或优化。

<!--more-->

相比Picgo优点：

1. 预处理模式支持水印、压缩、格式转换、移除EXIF信息。再也不用单独转换图片格式再重新上传了！
2. 切换同一图床不同配置。强迫症的福音、懂得都懂！
3. mini模式的。桌面会出现一个悬浮小球，把图片拉到这上面可以上传图片，不需要开大窗。且可以自定义图片。

![mini模式](https://r2.snbing.com/img/posts/f234875f2140a761.webp)

![图片预处理设置](https://r2.snbing.com/img/posts/915a26706c1f8ee3.webp)

## 配合Typora使用

### Windows

进入Typora设置界面，选择图像，将上传服务设置为`PicGo(app)`，然后在`PicGo路径`中填写PicList的安装路径，如下图所示：

![image-20240217234210185](https://r2.snbing.com/img/posts/df7d7b052737ffea.webp)

### MacOS

进入Typora设置界面，选择图像，将上传服务设置为`Custom Command`，然后在`Command`中填写`/Applications/PicList.app/Contents/MacOS/PicList upload`。
