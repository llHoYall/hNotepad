---
layout: post
title: Module - sys
category: python
tags: python
---

&nbsp;

# Module - sys

#### Attributes

- **argv** : 파이썬 스크립트로 넘어온 인자의 리스트이다. 0번째는 스크립트의 절대 경로이다.
- **copyright** : 설치된 파이썬의 저작권을 나타낸다.
- **modules** : 현재 로딩된 모듈들을 딕셔너리 형태로 나타낸다.
- **path** : 모듈을 찾을 때 참조하는 경로를 나타낸다.
- **prefix**, **exec_prefix** : 파이썬이 설치된 경로이다.
- **stdin**, **stdout**, **stderr** : 표준 입력, 출력, 에러 스트림에 해당하는 파일 객체를 나타낸다.
- **version** : 설치된 파이썬의 버전을 나타낸다.

#### Methods

- **exc_info()** : 현재 발생한 예외 정보를 튜플로 반환한다. 예외가 없는 경우 None을 반환한다.
- **exit([*arg*])** : 프로세스를 종효한다. arg가 0일 경우 정상적으로 종료되고, 0이 아닌 경우에는 비정상 적으로 종료된다.
- **getdefaultencoding()** : 현재 사용 중인 기본 문자열 인코딩을 반환한다.
- **getrefcount(*object*)** : 객체의 레퍼런스 카운트 값을 반환한다. 일반적으로 임시 객체가 참조하는 경우도 포함된다.
- **getwindowsversion()** : 현재 윈도우의 버전을 튜플로 반환한다.

