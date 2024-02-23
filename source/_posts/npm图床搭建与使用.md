---
title: npm图床搭建与使用
abbrlink: 38779
date: 2023-09-24 21:55:59
tags: npm
categories: 折腾记录
---

由于各种原因，已经启用npm图床，改为自建图床！

<!--more-->

首先我们需要登录Github并且创建一个仓库，本文取名为"benjamin-cdn"。

## npm注册&获取Token

1. 首先需要注册一个 npm 的账号并完成邮箱验证。访问：[npm 注册页面](https://www.npmjs.com/signup/)

2. 在本地将我们在Github新建的仓库克隆下来
   ```bash
   git clone git@github.com:[username]/[AssetsRepo].git
   #或者
   git clone https://github.com/[username]/[AssetsRepo].git
   ```

3. 在克隆仓库的文件夹内打开终端，属于以下指令切换回原生源
   ```bash
   npm config set registry https://registry.npmjs.org
   ```

4.  添加本地npm用户配置
   ```bash
   # 仅第一次使用需要添加用户，之后会提示你输入你的npm账号密码以及注册邮箱
   npm adduser
   # 非第一次使用直接登录即可，之后会提示你输入你的npm账号密码以及注册邮箱
   npm login
   ```

5. 运行`npm`初始化指令，把整个图床仓库打包，按照指示进行配置，注意需要事先确认你的包名没有和别人已发布的包重复，可以在npm官网搜索相应包名，搜不到就说明还没被占用。
   ```bash
   npm init
   ```

   最后会输出一段`package.json`，请求确认，输入`yes`即可。

6. 此时输入发布指令，我们就可以把包发布到npm上
   ```bash
   npm publish
   ```

7. 登录[npm官网](https://www.npmjs.com/)，右上角`头像`-`Access Tokens`-`Generate New Token`。生成`npm Token`。（`npm Token`只会显示一次，请妥善保管）

8. 登录Github并访问文章开始创建的仓库，添加一个名为`NPM_TOKEN`的`secrets`，把获取的Npm的 Access token输入进去

9. 在本地仓库文件夹下新建`[AssetsRepo]/.github/workflows/autopublish.yml`
   ```yaml
   name: Node.js Package
   # 监测图床分支，2020年10月后github新建仓库默认分支改为main，记得更改
   on:
     push:
       branches:
         - master
   
   jobs:
     publish-npm:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v2
         - uses: actions/setup-node@v1
           with:
             node-version: "12.x"
             registry-url: https://registry.npmjs.org/
         - run: npm publish
           env:
             NODE_AUTH_TOKEN: ${{secrets.npm_token}}
   ```

10. 在本地的仓库文件夹下打开终端，运行以下指令，上传新增内容至github，即可触发部署。
    ```bash
    # 将更改提交
    git add .
    git commit -m "npm publish"
    # 更新package版本号
    npm version patch
    # 推送至github触发action
    git push
    ```

    > 此处的四行指令顺序严格。
    > 每次更新 npm 图床都需要先修改`[AssetsRepo]\package.json`里的`version`,也就是版本号。
    > 而`npm version patch`即为更新 package.json 里的版本号的指令，效果是末尾版本号+1，例如`0.0.1=>0.0.2`、`1.1.3=>1.1.4`。免去了打开`package.json`再修改版本号的麻烦。（大版本更新还是需要手动改的）
    > 更新 npm 图床务必要记得更新`package.json`里的版本号！

## 使用

1. jsdelivr+npm的图片引用和jsdelivr+github很相似，例如我在`[AssetsRepo]`仓库里存放的`/img/index.png`
   ```YAML
   # jsDelivr+github链接
   https://cdn.jsdelivr.net/gh/[GithubUserName]/[AssetsRepo]/img/index.png
   # jsDelivr+npm链接
   https://cdn.jsdelivr.net/npm/[NpmPackageName]/img/index.png
   ```

2. jsDelivr+Npm依然有100MB的包大小限制，但是NPM有丰富的国内节点。可以挑选一个使用。个人推荐知乎的。没有大小限制，而且也很稳定。
   ```YAML
   【jsd出品，网宿国内节点】
   https://cdn.jsdelivr.net/npm/:package@:version/:file
   【unpkg 自建】
   https://cdn.cbd.int/:package@:version/:file
   ```

3. 当然你也可以利用[unpkg](https://unpkg.com/)自建。(UNPKG是一个内容源自npm的全球快速CDN。它部署在cloudflare上，在大陆地区访问到的是香港节点。所以速度也不错。)
   ```YAML
   https://unpkg.com/:package@:version/:file
   ```

   
