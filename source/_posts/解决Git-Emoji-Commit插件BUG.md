---
title: 解决Git-Emoji-Commit插件BUG
categories: 折腾记录
abbrlink: 145
date: 2024-02-01 17:52:56
tags:
index_img: https://r2.snbing.com/img/cover/101193d7181cc883.webp
sticky:
comment:
---

Visual Studio Code有个插件，Git Emoji Commit 中文版，可以在commit时添加emoji表情。但是最近出现BUG，无法点击。

<!--more-->

上网搜了一下，发现很多朋友都遇到这个问题。[选中后不显示相应的emoji](https://github.com/maixiaojie/git-emoji-zh/issues/33)。

不过有网友已经解决了，方法如下：

在`.vscode\extensions\maixiaojie.git-emoji-zh-1.1.9\out`目录下打开`extension.js`文件第23行：

```diff
+ return repository.rootUri.path === uri.rootUri.path;
- return repository.rootUri.path === uri._rootUri.path;
```

> 删除rootUri前面的下划线即可！

重启Visual Studio Code，搞定！
