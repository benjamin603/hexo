---
title: LskyPro&PicGo配置
categories: 折腾记录
tags: PicGo
abbrlink: 60266
date: 2024-02-01 16:42:36
index_img:
sticky:
comment:
---

之前已经搭建好兰空图床2.0版，博客写作平时使用`typora`来完成，所以打算通过`Picgo`+Typora并配合图床实现文章图片自动上传
<!--more-->

## 获取Tokens

我们可以通过在线POST来获取Tokens，这里推荐一个在线的网页：http://coolaf.com/zh/tool/gp

- 测试url：图床后台接口地址+tokens，如：`https://img.snbing.com/api/v1/tokens`
- POST参数：`email=邮箱&password=密码`

## PicGo配置

1. Picgo-插件设置搜索`lankong`并安装插件；
2. 配置插件参数：
   - `图床配置名`：任意填写
   - `Lsky Pro Version`：在下拉菜单中选择 Lsky Pro 版本，`V1` 还是 `V2`，默认 `V1`
   - `Server`：填写图床地址，注意不要以 `/` 结束
   - `Auth token`：使用 `Bearer `拼接
   - `Strategy ID`：存储策略 ID，如果是 V1 或 V2 使用默认存储策略的用户，请留空；除非你知道具体 ID，否则请留空
   - `Album ID`：相册 ID，只针对 V2 有效
   - `Permission`：图片权限，公开还是私有，默认是私有
   - `Sync Delete`：同步删除选项，只支持 `V2`，开启后在 PicGo 相册中删除图片可同步删除图床上的文件，默认关闭



### Well Done!
