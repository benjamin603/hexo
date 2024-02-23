---
title: Hexo备份到Github分支
tags: Hexo
cover: 'https://cdn.jsdelivr.net/npm/snailll-cdn/img/cover/20220315815497.webp'
categories: 折腾记录
description: 如果你有多设备来写Hexo博客，或者有需要备份Hexo源文件的需求，那么这个办法可能是最简单最方便的！
abbrlink: 16665
date: 2022-12-09 16:50:52
---

## 前言

如果你有多设备来写`Hexo`博客，或者有需要备份`Hexo`源文件的需求，那么这个办法可能是最简单最方便的！

## 备份

1. 将自己的Github项目克隆到本地；

2. 将除了`.git`以外的所有文件删除；

3. 拷贝自己本地`Hexo`源文件到上述文件夹；

4. 检查`.gitignore`， 包含以下需要忽略的内容：
   ```yaml
   .DS_Store
   Thumbs.db
   db.json
   *.log
   node_modules/
   public/
   .deploy*/
   ```

5. 创建并切换到新的备份分支（例：`bakcup`）：
   ```bash
   git checkout -b backup
   ```

6. 备份至Github：
   ```bash
   git add --all
   git commit -m "注释文字"
   git push -u origin backup
   ```

此时我们的Github仓库有了两个分支：

- `main`：托管静态网页
- `backup`：备份Hexo源文件

## 注意事项

如果主题是从Github克隆下来的，则会因为主题自身存在的`.git`文件夹导致无法成功上传主题文件。
解决办法：清理缓存，删除主题中的`.git`文件

```bash
git rm --cached "文件夹名字"
```

当然，我们也可以手动删除`.git`文件！

**Done！**
