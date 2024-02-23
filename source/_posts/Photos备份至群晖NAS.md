---
title: iPhone Photos备份至群晖NAS
categories: 折腾记录
tags:
  - iPhone
  - Photos
abbrlink: 35839
date: 2024-02-01 22:33:39
index_img: https://r2.snbing.com/img/cover/5d518828ff221e17.webp
sticky:
comment:
---

本文用来记录说明如何将iPhone Photos备份到Synology NAS。

<!--more-->

> 我想把iPhone上的照片和影片備份到Synology中，但是始終找到辦法完成這個任務。有沒有什麽快速的方法能幫助我備份iPhone到Synology？
>
> \- 來自Reddit的提問

现在对于手机拍照的要求越来越高了，导致手机照片体积也越来越大。而且几乎80%的图片都存放在iPhone上，为了保护照片的安全，除了iCloud备份外，还需要另外一个物理存储空间，这个时候Synology NAS就排上用场了！

## Synology NAS设置共享文件夹

登录Synology NAS，点击`File Station`，创建一个用来存放iPhone Photos的文件夹

## Windows设置

1. 使用`Windows + I`快捷键打开「设置」，在左侧菜单中选择「网络和 Intetnet」，然后点击右侧的「高级网络设置」选项。
2. 选择「高级共享设置」，然后在「专用网络」下启用「网络发现」开关。
3. （可选）如果你计划与其他网络设备共享文件，可以打开「文件和打印机共享」开关。
4. 网络发现在「公共网络」上默认关闭，在「专用网络」上默认开启。你还可以在「专用网络」上选择或取消勾选「自动设置网络连接的设备」。

![高级共享设置](https://r2.snbing.com/img/2024/02/65bbb03daf2e4.png)

## iPhone设置

DS file非常适合管理存储在Synology NAS上的文件，例如，可通过安全HTTPS连接在NAS和Android设备之间上传和下载文件，或执行基本编辑任务。此外，DS file对于随时浏览图片、观看视频或查看工作文档也非常有用。

1. 在App Store搜索`DS file`安装并登录；

2. 点击左上角更多（三横线图标），点击`照片备份` ，这时会要求再次登录NAS，登录后选择[Synology NAS设置共享文件夹](#Synology-NAS设置共享文件夹)创建的文件夹

   > 建议连接wifi备份，以免浪费移动流量！

以上是关于iPhone备份到Synology NAS的全部内容，备份iPhone到Synology前，您需要先将Synology映射到Internet，然后在透过DS file将iPhone照片备份到Synology。
