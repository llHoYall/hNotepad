---
layout: post
title: Help
category: vim
tags: vim
---

$~$

# Help

### Get Specific Help

도움말을 보려면 다음의 명령어를 사용한다.

- :help {cmd} - N 모드 명령어
- :help v\_{cmd} - V 모드 명령어
- :help i\_{cmd} - I 모드 명령어
- :help :{cmd} - C 모드 명령어
- :help c\_{cmd} - C 모드 편집 명령어
- :hep -{arg} - vim 명령어 인자
- :help 'option' - vim 옵션
- :help /{RegExp} - 정규표현식

명령어 부분의 입력을 할때, control키 조합은 '-', 각 조합의 사이는'\_'로 연결한다.

또, 정확한 명령어를 모르는 경우 일부분만 입력하고 \<CTRL-d>를 입력하면 매칭되는 목록을 보여준다.

예를 들면 N 모드에서 다음과 같이 입력한다.

> :h[elp] ctrl-w\_n
> :h[elp] ctrl-r\_ctrl-f

$~$

### Move and Jump

도움말 창에서 커서의 이동 혹은, 다른 태그로의 이동은 다음의 키를 입력한다.

- h - 왼쪽
- j - 아래쪽
- k - 위쪽
- l - 오른쪽
- \<CTRL-]> - 커서가 위치한 태그로 이동
- \<CTRL-t> - 되돌아 가기
- :tags - 이동한 태크 목록을 보여준다.

$~$

### Close

도움말을 종료하려면 다음의 명령어를 사용한다.

- :q


