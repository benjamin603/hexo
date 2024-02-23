---
title: Docker搭建Twikoo
tags: Twikoo
categories: 折腾记录
abbrlink: 48744
date: 2023-12-04 10:40:46
index_img: https://r2.snbing.com/img/cover/7bb706d6cf5c94eb.webp
---

一个简洁、安全、免费的静态网站评论系统。
A simple, safe, free comment system.

项目地址：https://github.com/twikoojs/twikoo

文档地址：https://twikoo.js.org/

<!--more-->

## 部署

使用以下命令搭建：

```sh
docker run --name twikoo -e TWIKOO_THROTTLE=1000 -p 8080:8080 -v ${PWD}/data:/app/data -d imaegoo/twikoo
```

> 这里默认使用`8080`端口，如果服务器该端口已经被占用，请修改为其他未被使用的端口。

我在服务器部署了[1Panel](https://1panel.cn)，我们来设置反向代理以及绑定域名。

1. 将域名解析到服务器地址，例：`tk.snbing.com` > `43.xxx.xxx.xxx`；

2. 在`1Panel`后台 - 网站 - 创建网站 - 反向代理：

   - 主域名 - 填入将使用的域名，例：`tk.bing.sn.cn`
   - 代号 - 随意 填写
   - 代理地址 -127.0.0.1 + 端口

3. 访问域名地址，得到如下结果表示部署成功！
   ```html
   {"code":100,"message":"Twikoo 云函数运行正常，请参考 https://twikoo.js.org/frontend.html 完成前端的配置","version":"1.6.26"}
   ```

>  因为我在服务器部署了[1Panel](https://1panel.cn)，端口为`8080`，与Twikoo端口冲突，导致无法访问。所以将容器删掉，重新创建容器并配置新的端口，即可！

## 替换表情包

**Twikoo后台** - **插件** - **EMOTION_CDN**可以自定义表情CDN，默认为https://owo.imaegoo.com/owo.json

[表情速查](https://emotion.xiaokang.me/)这里有大部分表情供我们使用，除了预览还有Twikoo代码直接使用感谢作者的分享！

![QQ表情](https://r2.snbing.com/img/2024/02/image-20240202100812970.png)

