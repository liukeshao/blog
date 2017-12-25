---
title: brew安装及常用命令
date: 2017-04-17 23:46:11
tags:
  - brew
categories:
  - mac
---

brew 安装及常用命令

<!-- more -->
1.安装（需要ruby）
   ```bash
   ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```
2.搜索：`brew search xxx`，所有的后台服务brew基本都有，例如：nginx、tomcat、mysql等
3.查询：`brew info xxx`，查看服务的基本信息，是否安装、启动命令、配置信息等
4.更新：`brew upadate`，更新Homebrew自己，使得5、6操作有意义
5.检查过时：`brew outdated`，返回所安装的软件有哪些可以升级，例如：mysql (5.7.17) < 5.7.18
6.升级：`brew upgrade`，真正的升级所安装软件，现在首先会执行brew update，所以没必要手动更新brew自己，brew upgrade xxx，可以单独更新某个软件
7.清理：`brew cleanup` ，清理以前安装过的版本，但是会缓存最后一个安装的版本
8.列表：`brew list`，罗列出已经安装过的软件 