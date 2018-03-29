---
layout: post
title: Docker - Commands
category: devtools
tags: docker
---

# Docker - Commands

Docker의 명령은 `docker <commad>`의 형식으로 사용한다. 또한, docker 명령은 root 권한으로 실행해야 한다.

### 1. search - 이미지 검색

> $ sudo docker search <image_name>

사용 예

> Ex) $ sudo docker search ubuntu

### 2. pull - 이미지 받기

> $ sudo docker pull <image_name>:<tag>

사용 예

> Ex) $ sudo docker pull ubuntu:latest

### 3. images - 이미지 목록 출력

> $ sudo docker images

### 4. run - 컨테이너 생성

> $ sudo docker run <option> <image_name> <command>

사용 예

> $ sudo docker run -i -t --name hi ubuntu /bin/bash

- `-i` : interactive
- `-t` : pseudo-tty
- `--name` : container name

ubuntu 이미지를 hi라는 이름의 컨테이너로 생성한 뒤, 이미지 안의 `/bin/bash` 명령을 실행한다.

### 5. ps - 컨테이너 목록 출력

> $ sudo docker ps

사용 예

> $ sudo docker ps -a

- `-a` : 정지된 컨테이너까지 출력한다.

### 6. start - 컨테이너 시작

> $ sudo docker start <container_name>

사용 예

> $ sudo docker start hi

### 7. restart - 컨테이너 재시작

> $ sudo docker restart <container_name>

사용 예

> $ sudo docker restart hi

### 8. attach - 컨테이너 접속

> $ sudo docker attach <container_name>

사용 예

> $ sudo docker attach hi

### 9. exec - 외부에서 컨테이너 내부 명령 실행

> $ sudo docker exec <container_name> <command> <arguments>

사용 예

> $ sudo docker exec hi echo "Hello World!"

hi라는 이름의 컨테이너 안의 echo 명령을 "Hello World!"인자와 함께 실행한다.

### 10. stop - 컨테이너 정지

> $ sudo docker stop <container_name>

사용 예

> $ sudo docker stop hi

### 11. rm - 컨테이너 삭제

> $ sudo docker rm <container_name>

사용 예

> $ sudo docker rm hi

### rmi - 이미지 삭제

> $ sudo docker rmi <image_name>:<tag>

사용 예

> $ sudo docker rmi ubuntu:latest

