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

​	사용 예)

> Ex) $ sudo docker search ubuntu

### 2. pull - 이미지 받기

> $ sudo docker pull <image_name>:<tag>

​	사용 예)

> Ex) $ sudo docker pull ubuntu:latest

### 3. images - 이미지 목록 출력

> $ sudo docker images

### 4. run - 컨테이너 생성

> $ sudo docker run <option> <image_name> <command>

​	사용 예) ubuntu 이미지를 hi라는 이름의 컨테이너로 생성한 뒤, 이미지 안의 `/bin/bash` 명령을 실행한다.

> $ sudo docker run -i -t --name hi ubuntu /bin/bash

- `-d` : run container in background
- `-p <host port>:<container port>` : publish a container's port to the host
- `-i` : interactive
- `-t` : allocate pseudo-tty
- `-v <host path>:<container path>` : bind mount a volume
- `--name <string>` : container name

### 5. ps - 컨테이너 목록 출력

> $ sudo docker ps

​	사용 예)

> $ sudo docker ps -a

- `-a` : 정지된 컨테이너까지 출력한다.

### 6. start - 컨테이너 시작

> $ sudo docker start <container_name>

​	사용 예)

> $ sudo docker start hello

### 7. restart - 컨테이너 재시작

> $ sudo docker restart <container_name>

​	사용 예)

> $ sudo docker restart hello

### 8. attach - 컨테이너 접속

> $ sudo docker attach <container_name>

​	사용 예)

> $ sudo docker attach hello

### 9. exec - 외부에서 컨테이너 내부 명령 실행

> $ sudo docker exec <container_name> <command> <arguments>

​	사용 예) hi라는 이름의 컨테이너 안의 echo 명령을 "Hello World!"인자와 함께 실행한다.

> $ sudo docker exec hello echo "Hello World!"

### 10. stop - 컨테이너 정지

> $ sudo docker stop <container_name>

​	사용 예)

> $ sudo docker stop hello

### 11. rm - 컨테이너 삭제

> $ sudo docker rm <container_name>

​	사용 예)

> $ sudo docker rm hello

### 12. rmi - 이미지 삭제

> $ sudo docker rmi <image_name>:<tag>

​	사용 예)

> $ sudo docker rmi ubuntu:latest

### 13. build - 이미지 생성

> $ sudo docker build <option> <Dockerfile path>

​	사용 예)

> $ sudo docker build --tag hello:0.1 .

### 14. history - 이미지 히스토리 보기

> $ sudo docker history <image_name>:<tag>

​	사용 예)

> $ sudo docker history hello:0.1

### 15. cp - 파일 꺼내기

> $ sudo docker cp <container_name>:<path> <host path>

​	사용 예) 현재 디렉토리에 nginx.conf 파일을 복사

> $ sudo docker cp hello-nginx:/etc/nginx/nginx.conf ./

### 16. commit - 컨테이너의 변경사항을 이미지로 생성

> $ sudo docker commit <option> <container_name> <image_name>:<tag>

​	사용 예)

> $ sudo docker commit -a "HoYa <hoya128@gmail.com>" -m "add files" hello-nginx hello:0.2

- `-a <string>` : author
- `-m <string>` : commit message

### 17. diff - 컨테이너 변경파일 출력

> $ sudo docker diff <container_name>

​	사용 예)

> $ sudo docker diff hello-nginx

### 18. inspect - 세부 정보 출력

> $ sudo docker inspect <image_name or container_name>

​	사용 예)

> $ sudo docker inspect hello-nginx

