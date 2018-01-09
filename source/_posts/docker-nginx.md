---
title: docker-nginx
date: 2018-01-09 09:07:49
categories:
  - docker
tags:
  - docker
  - nginx
---

nginx installation on docker container

<!-- more -->

1. 拉取nginx image

   ```bash
   docker pull nginx:latest
   ```

2. 运行mysql

   ```bash
   docker run --name nginx \
     -p 80:80 \
     -v $HOME/docker/nginx/conf.d:/etc/nginx/conf.d \
     -v $HOME/docker/nginx/html:/usr/share/nginx/html \
     -v $HOME/docker/nginx/log:/var/log/nginx \
     -d nginx:latest
   ```

   `--name` 指定docker容器名称
   `-p` 将容器的80端口映射到宿主机的80，格式 `主机端口`:`容器端口`
   `-v` $HOME/docker/nginx/conf.d:/etc/nginx/conf.d，映射nginx 配置目录
   `-v` $HOME/docker/nginx/html:/usr/share/nginx/html，映射nginx 静态文件目录
   `-v` $HOME/docker/nginx/log:/var/log/nginx 映射nginx日志目录
   `-d` 后台启动

   > conf demo
   >
   > 在 $HOME/docker/nginx/conf.d:/etc/nginx/conf.d 新建以`.conf`结尾的配置文件，例如：test.conf

   ```shell
   server {
       listen       80;
       server_name www.test.com;
       location / {
           proxy_pass http://test_server;
       }
    }
    upstream test_server {
        # 宿主机ip:port
        server 192.168.2.42:6767;
    }
   ```


3. 启动/停止nginx

   ```bash
   # 停止 nginx
   docker stop nginx

   # 启动 nginx
   docker start nginx
   ```

