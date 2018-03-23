---
layout: post
title: Makefile
category: devtools
tags: makefile
---

&nbsp;

# Makefile

기본적인 문법은 다음의 형태로 사용된다.

```makefile
target: dependency
	command
```



##### PHONY Targets

동일한 이름의 파일을 사용한 경우의 충돌을 피하기 위한 목적과, make 성능 향상을 위한 목적으로 사용한다.

PHONY target은 다른 target의 dependency가 되어서는 안된다. target과 동일한 이름의 file이 있는지 없는지 신경쓰지 않고 무작정 command를 실행한다.

```makefile
.PHONY: all clean
```



명령의 앞에 `-` 를 붙이면, 명령의 수행이 오류가 있더라도 중지하지 않고, 다음 명령을 실행한다.

