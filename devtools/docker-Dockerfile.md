---
layout: post
title: Docker - Dockerfile
category: devtools
tags: docker
---

# Docker - Dockerfile

Dockerfile은 Docker 이미지 설정 파일이다. Dockerfile에 설정된 내용대로 이미지를 생성한다.

예를 들면 다음과 같다.

```dockerfile
# Dockerfile
# 우분투 14.04를 기반으로 nginx 서버를 설치한 Docker 이미지를 생성.
FROM ubuntu:14.04
MAINTAINER HoYa <hoya128@gmail.com>

RUN apt-get update
RUN apt-get install -y nginx
RUN echo \ndaemon off;" >> /etc/nginx/nginx.conf
RUN chown -R www-data:www-data /var/lib/nginx

VOLUME ["/data", "/etc/nginx/site-enabled", "/var/log/nginx"]

WORKDIR /etc/nginx

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
```

위 Dockerfile로 이미지를 생성한 후 실행을 한다.

> $ sudo docker build --tag hello:0.1 .
>
> $ sudo docker run --name hello-nginx -d -p 80:80 -v /root/data:/data hello:0.1

