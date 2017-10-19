---
layout: post
title: Getting Started
category: vim
tags: vim
---

&nbsp;

# Getting Started

### Installation

- on MAC

  > $ brew install vim

- on Linux

  > $ apt-get install vim

&nbsp;

### Run

실행은 다음과 같이 한다.

> $ vim [*arguments*] \[*files* ...]

vim을 실행하면 기본 설정 파일로 실행이 된다.

다음과 같이 하면, 깨끗한 상태로 실행이 된다.

> $ vim -u NONE -N



자주 사용하는 arguments 들은 다음과 같다.

- -N : Vi와 호환되지 않는다. nocompatible.
- -u \<*vimrc*> : 명시한 설정파일로 실행을 한다.
- --noplugin : 플러그인 스크립트를 실행하지 않는다.
- -p : 파일 별로 하나씩 N개의 탭을 연다. 
- -o : 파일 별로 하나씩 N개의 수평분할 창을 연다.
- -O : 파일 별로 하나씩 N개의 수직분할 창을 연다.

&nbsp;

### Tip

1. 특수 문자 입력 방법

   \<CTRL-v> o### : 8진수 ascii 코드 입력.

   \<CTRL-v> ### : 10진수 ascii 코드 입력.

   \<CTRL-v> x## : 16진수 ascii 코드 입력.

   `:as[cii]` 명령을 입력하면 커서가 위치한 문자의 ascii 코드 값을 알 수 있다.

2. 숫자 증감

   \<CTRL-a> : 커서 뒤쪽에 있는 숫자를 1 증가한다.

   \<CTRL-x> : 커서 뒤쪽에 있는 숫자를 1 감소한다.

&nbsp;

### Reference

- http://www.vim.org
- http://vimcasts.org


