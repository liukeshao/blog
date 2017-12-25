---
title: docker 安装 mysql
date: 2017-12-25 15:27:15
tags:
  - docker
categories:
  - docker
---

docker  安装 mysql 教程

<!-- more -->

1. 拉取mysql image

  ```bash
  docker pull mysql:latest
  ```

2. 运行mysql

  ```bash
  docker run --name mysql \
  -p 3306:3306 \
  -v /Users/ks/docker/mysql/data:/var/lib/mysql \
  -v /Users/ks/docker/mysql/conf:/etc/mysql/conf.d \
  -e MYSQL_ROOT_PASSWORD=lovelive \
  -d mysql:latest
  ```

  `--name` 指定docker容器名称
  `-p` 将容器的3306端口映射到主机的3306，格式 `主机端口`:`容器端口`
  `-v` /Users/ks/docker/mysql/data:/var/lib/mysql，映射mysql data目录
  `-v` /Users/ks/docker/mysql/conf:/etc/mysql/conf.d，映射mysql config目录
  `-e` 指定初始化root密码
  `-d` 指定mysql版本

3. 启动/停止mysql

   ```bash
   # 停止 mysql
   docker stop mysql

   # 启动 mysql
   docker start mysql
   ```
