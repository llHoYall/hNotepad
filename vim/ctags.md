---
layout: post
title: ctags
category: vim
tags: [vim, tool]
---

&nbsp;

# ctags

코드 분석 등을 도와주는 툴이다. vim에서 연동하여 사용할 수 있다.

&nbsp;

### Installation

- on Windows

  > $ choco install ctags -y

&nbsp;

### Using

분석을 원하는 디렉토리에서 다음의 명령을 수행한다.

> $ ctags *

하위 디렉토리까지 분석을 하려면 다음의 명령을 수행한다.

> $ ctags -R

분석이 끝나면 tags란 파일이 생긴다.

Vim에서 이 tags 파일을 추가해준다.

> :set tags+={*path*}

&nbsp;

#### on Vim

- **\<CTRL-]>** - 커서 위치의 함수가 정의된 파일로 이동.
- **\<CTRL-t>** - 이전 위치로 이동.
- :ts[elect] \<*func_name*> - 해당 이름의 함수 목록을 보여준다. 선택해서 이동할 수 있다.
- :tj[ump] \<*tag_name*> - 해당 이름의 태그로 이동.
- :stj[ump] \<*tag_name*> - 해당 이름의 태그를 분할 창으로 연다.
- :[#]po[p] - Jump to # older entry in tag stack. (default 1).
- :tn[ext] - 다음 함수로 이동.
- :tp[revious] - 이전 함수로 이동.
- :tf[irst] - 가장 처음에 찾은 함수로 이동.
- :tl[ast] - 가장 마지막에 찾은 함수로 이동.