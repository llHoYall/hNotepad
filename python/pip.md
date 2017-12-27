---
layout: post
title: pip
category: python
tags: python
---

&nbsp;

# pip

pip는 파이썬의 패키지 관리툴이다.

#### Install Packages

- Latest Version

> $ pip install \<*packages*\>

- Upgrade

> $ pip install [--upgrade] \<*packages*\>

- Specific Version

> $ pip install \<*packages*==*version*\>
> $ pip install \<*packages*\>=*version*\>
> $ pip install \<*packages*\<*version*\>

`requirements.txt` 파일에 필요한 패키지나 모듈의 이름을 넣어놓고, 다음과 같이 한꺼번에 설치를 할 수도 있다. 일반적으로 사용하는 파일명이며 원하면 바꿔도 된다.

> $ pip install -r requirements.txt

#### Upgrade pip

> $ pip install -U pip setuptools

#### List Installed Packages

> $ pip list \[--format=columns\] \[--outdated\]

#### Search Packages

> $ pip search \<*packages*\>

#### Output Installed Packages

설치된 패키지를 세부 버전까지 동일하게 파일로 저장할 수 있다. 파일명은 원한다면 바꿔도 된다.

> $ pip freeze > requirements.txt

#### Uninstall Packages

> $ pip uninstall \<*package*\>