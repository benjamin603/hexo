---
title: Ubuntu部署1Panel
categories: 折腾记录
tags: 1Panel
abbrlink: 6110
date: 2024-02-01 10:40:51
index_img: https://r2.snbing.com/img/cover/e277dd1e05688a22.webp
sticky:
---

阿里云ECS和NAS都使用了Docker部署服务，刚好接触了[1Panel](https://1panel.cn/)面板，相对于宝塔面板，很是喜欢!

<!--more-->

## 部署

```bash
curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sudo bash quick_start.sh
```

一条代码即可搞定！

> 1Panel面板后台账号不支持使用过于简单的密码，在部署1Panel时却没有这种限制！

## 配置

### 添加备份账号

目前将服务器一些应用、数据备份在阿里云OSS，后期会增加备份到Nas。

### 计划任务

1Panel支持定时备份应用、网站、数据库等操作，挺方便，再也不担心服务器挂了导致数据丢失！

## 应用

- `Memos` - 一款隐私优先的轻量级笔记服务，轻松捕捉并分享您的精彩想法。
- `Typecho` - 用来搭建Plog相册站点
- `Lsky-Pro` - 自建图床
