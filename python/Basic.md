---
layout: post
title: Basic
category: python
tags: python
---

&nbsp;

# Basic

### Installation 

> https://www.python.org/downloads/

##### on Windows

관리자 권한 필요.

> $ choco install python -y
>
> $ refreshenv

##### on Mac

> $ brew install python -y

##### on Linux

> $ apt-get install python -y

### 종류

- CPython : C로 개발된 파이썬. 기본적으로 파이썬이라 하면 이것을 가리킨다.
- Jython : Java로 개발된 파이썬. JVM상에서 작동하며 자바랑 호환된다.
- IronPython : C#으로 개발된 파이썬. .net과 모노용.
- PyPy : 파이썬으로 개발된 파이썬. CPython보다 빠르게 실행하는 것을 목표로 한다.

### Main

```python
if __name__=="__main__":
    print("Hello World")
```

위 코드가 메인으로 실행 될 때만 해당 코드가 실행되며, 다른 모듈에서 import했을 때는 실행되지 않는다.

### Indentation

파이썬은 들여쓰기로 코드 블록을 만든다. 

상위 레벨 코드 끝에 colon을 붙이고, 하위 레벨 코드를 들여쓰는 방법을 사용한다. 같은 레벨에서는 정확히 같은 공백 혹은 탭을 사용해야 한다.

pep8에서는 4개의 공백을 권장한다.

### Comment

주석은 #을 사용한다.

```python
# This is a comment.
```

### Source Code Encoding

리눅스 환경에서 실행 파일 경로와 인코딩 방식을 명시한 예이다.

```python
#!/usr/bin/python
# coding: latin-1
# -*- coding: utf-8 -*-
```

소스 인코딩은 2, 3번째 라인처럼 coding 지시자를 사용하여 지정할 수 있고, 지정하지 않은 경우 ascii가 기본이다.

### Line Break

라인 끝에 backslash를 붙여서 다음 라인으로 코드가 이어짐을 명시할 수 있다.

