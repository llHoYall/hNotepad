---
layout: post
title: distutils
category: python
tags: python
---

&nbsp;

# distutils

distutils는 플랫폼에 종속되지 않고 프로그램을 배포해줄 수 있게 도와주는 툴이다.

단, 스크립트를 사용하기 때문에 플랫폼에 따라 스크립트를 따로 관리해줘야 한다.

### 기본 사용법

##### 배포용 스크립트

다음의 예제처럼 배포를 하고자 하는 내용을 스크립트로 작성하자. 관례적으로 setup.py라는 이름을 사용한다. 필요한 코드들은 모두 setup.py가 있는 곳에 있어야 한다.

```python
# setup.py

from distutils.core import setup

setup(
    name='test',
    version='1.0',
    py_modules=['test'],
)
```

##### 배포 절차

다음 명령을 실행하면 배포할 내용을 묶어 dist 디렉토리 안에 압축 파일로 만들어 준다. 이 압축 파일을 배포하면 된다.

소스코드 형태로 배포하려면 sdist (source distribution), 바이너리 형태로 배포하려면 bdist (binary distribution)를 사용한다. bdist를 사용하면 소스코드와 바이트코드가 함께 포함된다.

> $ python setup.py sdist
>
> $ python setup.py bdist

윈도우즈용으로 인스톨러를 만들어 배포하려면 bdist_wininst, 리눅스용으로 인스톨러를 만들어 배포하려면 bdist_rpm을 사용한다.

> $ python setup.py bdist_wininst
>
> $ python setup.py bdist_rpm

##### 설치

배포한 압축 파일을 받은 사용자는 압축을 풀고 다음 명령을 실행하여 설치를 한다.

> $ python setup.py install

### setup.py 파일 작성법

