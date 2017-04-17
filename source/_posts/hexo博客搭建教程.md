---
title: Hexo系列教程 mac版
date: 2017-04-17 15:13:01
tags: 
  - hexo 
  - github page
categories:
  - Hexo教程
---

# 概述 

介绍在mac下如何使用hexo搭建个人blog，并将blog部署到github page上。

 <!--more-->

# 安装

## 安装前提
- [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)

使用`brew`安装`nodejs`和`git`
```
brew install node
brew install git
```

## 安装 Hexo
```
npm install -g hexo-cli
```

# 建站

使用`hexo init [folder]`命令初始化blog
使用`hexo server`命令启动一个hexo服务，访问[http://localhost:4000/](http://localhost:4000/)查看效果
```shell
hexo init blog
cd blog
npm install
hexo server
```

# 配置

Hexo 有两份主要的配置文件，名称都为`_config.yml`
位于站点主目录下的我们将其称之为`站点配置`，提供hexo本身的配置
位于主题目录下的我们将其称之为`主题配置`，提供主题的相关配置
现在介绍`站点配置`

| 参数          | 描述                                       |
| ----------- | ---------------------------------------- |
| title       | 网站标题                                     |
| subtitle    | 网站副标题                                    |
| description | 网站描述                                     |
| author      | 作者                                       |
| language    | 网站使用语言，根据使用的主题来修改。                       |
| timezone    | 网站时区。Hexo 默认使用您电脑的时区。[时区列表](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。比如说：`America/New_York`, `Japan`, 和 `UTC` 。 |

# 部署

## 修改`站点配置`

```
deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
```
demo：
```
deploy:
  type: git
  repo: git@github.com:[username]/[username].github.io.git
  branch: master
```
## 安装 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)

```
cd blog
npm install hexo-deployer-git --save
```
## 部署到github page

使用`hexo d -g ` 将博客部署到github page，访问[username].github.io查看效果