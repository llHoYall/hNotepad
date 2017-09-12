---
layout: post
title: Getting Started
category: shell
tags: [shell, bash]
---

&nbsp;

# Getting Started

##### 현재 로그인 되어있는 shell 확인

> $ echo \$SHELL

&nbsp;

##### Shell script 작성

스크립트 파일의 시작을 다음과 같은 shebang으로 한다.

```sh
#!/bin/bash
echo "Hello World!"
```

&nbsp;

##### 파일 형식 확인

> $ file {*filename*}

&nbsp;

##### 문법 체크

> $ sh -n {*filename*}

&nbsp;

##### 파일에 실행 권한 부여

> $ chmod +x {*filename*}

&nbsp;

##### 실행

경로와 파일명을 사용하여 실행한다.

> $ {*path*}/{*filename*}
> $ ./{*filename*}

.은 현재 디렉토리를 의미한다.

&nbsp;

### Option

Shell 스크립트를 옵션과 함께 사용할 수 있다.

- -{option}
- \--{long\_option}
- — : 뒤로는 옵션이 존재하지 않음을 명시

