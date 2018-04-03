---
layout: post
title: Docker - Create Image
category: devtools
tags: docker
---

# Docker - Create Image

## Empty Base Image

Docker에서는 빈 베이스 이미지를 scratch 이미지라고 한다.

/dev/null 장치를 이용하여 빈 tar 파일을 만들어서 docker에 전달한다.

> $ tar cv --files-from /dev/null | sudo docker import - scratch

scratch 이미지는 비어있기 때문에 컨테이너로 생성되지 않는다.

hello라는 C 프로그램을 만들어 scratch에 넣어보자. scratch 이미지에는 아무런 라이브러리도 없으므로 static 바이너리로 컴파일 해야한다.

> $ gcc hello.c -static -o hello

Dockerfile을 만든다.

```dockerfile
FROM scratch
ADD ./hello /hello
CMD ["/hello"]
```

scratch 이미지를 기반으로 새로운 이미지를 생성한다.

> $ sudo docker build --tag hello:0.1 .

hello:0.1 이미지로 컨테이너를 생성한다.

> $ sudo docker run --rm hello:0.1

C 프로그램이 구동되면 정상적으로 실행된 것이다.

