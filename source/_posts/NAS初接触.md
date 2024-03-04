---
title: NAS初接触
tags: NAS
categories: 折腾记录
abbrlink: 43999
date: 2023-10-06 08:25:06
sticky: 
index_img: 
---

## 前言

之前经历过因为换手机并且忘记icloud恢复密钥，导致使用十多年的AppleID差点丢失！

<!--more-->

最后回归属地补办了之前已经停用的手机号才找回账号。

丢失AppleID期间造成了很多的不便：

- 通讯录全无
- Apple Store付费购买/买断的应用没法使用
- iCloud家庭组共享相册无法找回
- 还有很多很多很多......

当时就觉得将所有的资料存上云也并不一定是安全的，所以就有了使用NAS的想法！

## NAS

黑群晖DS920+，DSM 7.1.1-42962。

- 两块块3T硬盘组`raid1`
- 一块4T硬盘直接`basic`

## 入门操作

### 启动SSH功能

控制面板搜索SSH并开启。

### 添加套件源

- 我不是矿神 - `https://spk7.imnks.com/`

### 备份windows11系统

详见：[windows11系统备份](/posts/6081.html)

### iPhone Photos备份至群晖NAS

详见：[iPhone Photos备份至群晖NAS](/posts/35839.html)
