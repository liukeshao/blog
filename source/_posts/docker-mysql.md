---
title: mysql installation on docker container
date: 2017-12-25 15:27:15
categories:
  - docker
tags:
  - docker
  - mysql
---

mysql installation on docker container

<!-- more -->

1. 拉取mysql image

  ```bash
  docker pull mysql:latest
  ```

2. 运行mysql

  ```bash
  docker run --name mysql \
    -p 3306:3306 \
    -v $HOME/docker/mysql/data:/var/lib/mysql \
    -v $HOME/docker/mysql/conf:/etc/mysql/conf.d \
    -e MYSQL_ROOT_PASSWORD=lovelive \
    -d mysql:latest
  ```

  `--name` 指定docker容器名称
  `-p` 将容器的3306端口映射到主机的3306，格式 `主机端口`:`容器端口`
  `-v` $HOME/docker/mysql/data:/var/lib/mysql，映射mysql data目录
  `-v` $HOME/docker/mysql/conf:/etc/mysql/conf.d，映射mysql config目录
  `-e` 指定初始化root密码
  `-d` 后台启动

3. 启动/停止mysql

   ```bash
   # 停止 mysql
   docker stop mysql

   # 启动 mysql
   docker start mysql
   ```

