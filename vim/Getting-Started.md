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

- with default setting file (.vimrc)

  > $ vim

- with factory settings

  >  $ vim -u NONE -N

- with custom setting file

  >  $ vim -u {*custom\_setting\_file*}.vim

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


