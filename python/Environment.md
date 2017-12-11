---
layout: post
title: Environment
category: python
tags: python
---

&nbsp;

# Environment

## virtualenv

각각의 프로젝트별로 개발 환경을 분리하여 필요 패키지 관리 등을 편리하게 할 수 있다.

##### Installation

설치는 간단하게 pip를 사용한다.

> $ pip install virtualenv

##### Make Virtual Environment

가상 환경을 구성하고 싶은 root 디렉토리에서 다음 명령을 입력하면 해당 디렉토리 명으로 가상 환경이 생성된다.

> $ virtualenv \<*DIR_NAME*>

##### Activation

가상 환경 디렉토리로 이동하여 가상 환경을 구동한다.

> $ cd \<*DIR_NAME*>
>
> // MAC or Linux
>
> $ source bin/activate
>
> // Windows
>
> $ .\Scripts\activate

##### Using

이제 독립적인 환경하에서 필요한 각종 패키지를 설치하고 개발을 한다.

##### Deactivation

가상 환경에서 빠져나오려면 다음 명령을 사용한다.

가상 환경 사이를 옮겨다니며 작업을 할 때는 반드시 이 작업을 해줘야 가상 환경이 꼬이는 일이 없다.

> $ deactivate

&nbsp;

## Jupyter

노트북 형태로 파이썬 코드를 작성, 실행, 관리할 수 있는 도구이다.

##### Installation

역시 설치는 pip를 사용한다.

> $ pip install jupyter

##### Using

아래의 명령을 입력하면 자동으로 웹브라우저에서 실행이 된다.

> $ jupyter notebook

아래의 명령을 입력하면 현재 사용 가능한 kernel들을 확인할 수 있다.

> $ jupyter kernelspec list

##### Working with virtualenv

사용할 virtualenv를 activation한다.

jupyter에서 사용할 kernel을 만든다.

> $ ipython kernel install

만들어진 kernel의 디렉토리명과 kernel.json 파일의 "display_name"을 원하는 이름으로 변경한다.

jupyter notebook을 실행하여 새로 만든 커널로 사용하면 된다.

