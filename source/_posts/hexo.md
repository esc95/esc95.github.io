---
title: 从0开始搭建Hexo个人博客
date: 2021-12-01 01:01:01
tags:
---

> 搭建个人博客是每个程序员成长的必经之路，不但可以记录与分享自己在学习过程中 Get 到的新技能、新知识，还能顺便提高一下自己的文采。

# Hexo 简介

Hexo 是一款基于 Node.js 的静态博客框架，可方便快捷的托管于 GitHub 上，是搭建博客的首选框架。

根据[Hexo 官网](https://hexo.io/zh-cn/)介绍，主要有以下四大优点：

- 超快速度： Node.js 所带来的超快生成速度，让上百个页面在几秒内瞬间完成渲染。
- 支持 Markdown：Hexo 支持 GitHub Flavored Markdown 的所有功能，甚至可以整合 Octopress 的大多数插件。
- 一键部署：只需一条指令即可部署到 GitHub Pages, Heroku 或其他平台。
- 插件和可扩展性：强大的 API 带来无限的可能，与数种模板引擎（EJS，Pug，Nunjucks）和工具（Babel，PostCSS，Less/Sass）轻易集成

# Hexo 搭建步骤

## 安装 Git

Git 是目前世界上最先进的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。无论是个人代码管理还是团队合作开发中，学会 git 那都是百利而无一害的。如果对 git 还不是很了解，推荐去[廖雪峰老师的博客](https://www.liaoxuefeng.com/wiki/896043488029600)或者先看一下[Git Book](https://git-scm.com/book/zh/v2)的前三章。

```bash
# 安装命令
$ sudo apt-get install git

# 查看版本
$ git --version
```

## 安装 Node.js

Hexo 是基于 Node.js 环境运行的，所以需要安装 Node 环境及 npm 包管理工具。

```bash
# node安装命令
$ sudo apt-get install nodejs

# 查看node版本
$ node -v

# npm安装命令
$ sudo apt-get install npm

# 查看npm版本
$ npm -v
```

## 安装 Hexo

```bash
# 利用npm全局安装hexo脚手架
$ npm install -g hexo-cli

# 查看hexo版本
$ hexo -v

# 删除hexo
$ npm uninstall -g hexo-cli

# 查看npm全局版本
$ npm ls -g --depth=0
```

## 创建博客项目

到此为止，装好了 node 环境以及 hexo 框架，基本上前期的环境配置就完成了，接下来就可以创建自己的博客项目了。

```bash
# 新建一个文件夹，如名为blog
$ mkdir blog

# 进入blog文件夹
$ cd blog

# 初始化hexo
$ hexo init
```

初始化成功后，blog 文件夹下会出现如下文件：

- \_config.yml: 博客的核心配置文件（设置主体、标题等属性）
- package.json：项目所需的依赖包
- source：用来存放你的文章
- themes：放下下载的主题
- public：存放生成的页面
- scaffolds：生成文章的一些模板

```bash
# 安装所需依赖
$ npm install
```

安装成功后，会出现 node_modules 文件夹，文件夹内即安装的 package.json 内所有依赖包。接下来就可以配置并启动 hexo 了

```bash
# 清除缓存文件 (db.json) 和已生成的静态文件 (public)
$ hexo clean

# 生成静态文件，generate
$ hexo g

# 部署博客网站，deploy
$ hexo d

# 启动服务器，server
$ hexo s -g
```

运行成功后，浏览器打开`http://localhost:4000`便可看到你的 hexo 博客项目了，除了主题有点儿吃藕，还是挺不错的~

## 将 Hexo 部署到 GitHub

这一步，我们就可以将 hexo 和 GitHub 关联起来，也就是将 hexo 生成的文章部署到 GitHub 上，打开站点配置文件\_config.yml，翻到最后，修改为下面这样，其中 LeeDebug 改为你的 GitHub 账户名

```bash
deploy:
  type: git
  repo: https://github.com/LeeDebug/LeeDebug.github.io.git
  branch: master
```

这个时候需要先安装 deploy-git，也就是部署的命令,这样你才能用命令部署到 GitHub。

```bash
$ npm install hexo-deployer-git --save
```

部署项目

```bash
$ hexo clean
$ hexo g
$ hexo d
```

部署成功后，浏览器打开`http://esc95.github.io`，就能看到你的博客了

# 安装主题

首先下载主题包，如[butterfly](https://github.com/jerryc127/hexo-theme-butterfly)

```bash
npm i hexo-theme-butterfly
```

配置`_config.yml`文件

```bash
theme: butterfly
```

# 新建文章

首先修改`/scaffolds/post.md`文件模板，改为想要的形式，比如

```bash
---
title: {{ title }}
tags:
- Hexo
categorier:
- Hexo
keywords: "Hexo,笔记"
date: {{ date }}
description: "描述"
cover: https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/cover/default_bg.png
---
```

利用 post 模板新建文章

```bash
hexo new post 文章标题
```

随后在`source/_posts/`文件夹下会出现`文章标题`的文件夹和`文章标题.md`的 MarkDown 文件，文章内容在`*.md`文件内编辑即可

# 新增分类页

```bash
hexo new page categories
```

将`/source/categories/index.md/`这个文件改为以下内容

```bash
---
title: 分类
date: 2018-01-05 00:00:00
type: "categories"
---
```

# 新增标签页

```bash
hexo new page tags
```

将`/source/tags/index.md/`这个文件改为以下内容

```bash
---
title: 标签
date: 2018-01-05 00:00:00
type: "tags"
---
```
