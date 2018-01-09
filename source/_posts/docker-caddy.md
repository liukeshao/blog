---
title: caddy installation on docker container 
date: 2017-12-25 17:35:55
categories:
  - docker
tags:
  - docker
  - caddy
---

caddy installation on docker container 

<!-- more -->

1. pull image

   ```bash
   docker pull abiosoft/caddy
   ```

2. 运行caddy

   ```bash
   docker run --name caddy \
     -v $HOME/docker/caddy/Caddyfile:/etc/Caddyfile \
     -v $HOME/docker/caddy/.caddy:/root/.caddy \
     -p 80:80 \
     -p 443:443 \
     -d abiosoft/caddy:latest
   ```

   ​