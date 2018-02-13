---
layout: post
title: user management
category: os
tags: [os, linux, mac, unix]
---



# User Management

### 사용자 추가

- `useradd` : 새로운 사용자를 만들거나 기존 사용자의 정보를 업데이트 한다.
- `adduser` : 사용자를 시스템에 추가한다.

상세하게 옵션 설정을 해서 추가를 하려면 `useradd` 명령어를 사용하고, 간단하게 기본 설정으로 추가하려면 `adduser` 명령어를 사용한다.

> $ adduser \<account>

sudo 권한을 주려면 다음과 같이 한다.

> $ sudo adduser \<account> sudo

### SSH 설정

다음 패키지를 설치만 하면 된다.

> $ sudo apt install openssh-server

### Samba 설정

다음 패키지를 설치한다.

> $ sudo apt install samba

설정 파일을 편집한다.

> $ sudo vim /etc/samba/smb.conf

```sh
...

[user]
	comment = My samba server
	path = /home/user
	writeable = yes
```

이제 서비스를 재시작한다.

> $ sudo service smbd restart

### VNC 설정

다음 패키지를 설치한다.

> $ sudo apt install tightvncserver

비밀번호를 설정한다.

> $ vncserver

이제 tight vnc viewer로 원격 접속을 하면 된다. 어쩌고저쩌고:#과 같이 숫자가 있는 데, 이것이 세션 번호라고 보면 된다. tight vnc의 기본 포트는 5900이고, 여기에 이 세션 번호를 더해주면 접속할 수 있다. 

즉, Remote Host에 \<IP:Port>와 같이 입력을 해준다. IP가 192.168.0.7이고 세션 번호가 3이라고 하면 `192.168.0.7:5903`과 같다.

추가로, 열려있는 서버를 삭제하려면 `$ vncserver -kill :#`과 같이 한다.

