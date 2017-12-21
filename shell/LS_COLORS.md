---
layout: post
title: LS_COLORS
category: shell
tags: shell
---

&nbsp;

# LS_COLORS

ls 등의 명령어를 입력했을 때, 디렉토리나 파일의 확장자 별로 서로 다른 색상을 지정할 수 있다.

`.bashrc`나 `.zshrc`등 사용하는 shell의 설정 파일에 LS_COLORS 설정을 넣어준다.

문법은 다음과 같다.

> LS_COLORS="filetype=attr;color:filetype=attr;color..."

- filetype은 다음과 같이 사용한다.
  - fi : 일반 파일
  - di : 경로
  - lh : symbolic link
  - pi : FIFO (pipe)
  - so : 소켓
  - bd : block device
  - cd : character device
  - ex : 실행 파일
  - *.png : 확장자가 png인 파일
  - *.mp3 : 확장자가 mp3인 파일
- attribute는 다음과 같이 사용한다.
  - 0 : default
  - 1 : bold
  - 4 : underlined
  - 5 : blink
  - 7 : revert
- color는 다음과 같이 사용한다.
  - 31 : fg-red
  - 32 : fg-green
  - 33 : fg-orange
  - 34 : fg-blue
  - 35 : fg-purple
  - 36 : fg-cyan
  - 37 : fg-grey
  - 40 : bg-black
  - 41 : bg-red
  - 42 : bg-green
  - 43 : bg-orange
  - 44 : bg-blue
  - 45 : bg-purple
  - 46 : bg-cyan
  - 47 : bg-grey
  - 90 : fg-dark grey
  - 91 : fg-light red
  - 92 : fg-light green
  - 93 : fg-yellow
  - 94 : fg-light blue
  - 95 : fg-light purple
  - 96 : fg-turquoise
  - 100 : bg-dark grey
  - 101 : bg-light red
  - 102 : bg-light green
  - 103 : bg-yellow
  - 104 : bg-light blue
  - 105 : bg-light purple
  - 106 : bg-turquoise

사용 예는 다음과 같다.

>  export LS_COLORS=$LS_COLORS:"di=94:\*.sh=32:\*.ps1=32"

