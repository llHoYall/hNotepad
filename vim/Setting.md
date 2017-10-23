---
layout: post
title: Setting
category: vim
tags: vim
---

&nbsp;

# Setting

## Options

- :set - 현재 설정된 옵션들의 상태를 보여준다.
- :set *option* - 해당 옵션의 상태를 보여준다.
- :set all - 모든 옵션들의 상태를 보여준다.
- :set [no]*option* - 해당 옵션을 enable/disable 한다.
- :set *option*! - 해당 옵션의 상태를 toggle 한다.
- :set *option*=*value* - 해당 옵션에 값을 지정한다.

옵션 사이에 공백으로 구분하여 여러 옵션을 한 번에 설정할 수도 있다.



많이 사용하는 옵션들을 나열하였다.

- nu (number) - 라인 번호 표시.
- ai (autoindent) - 자동 들여쓰기. 이전 라인의 들여쓰기 만큼 들여쓴다.
- cindent - c 스타일 들여쓰기. 블록 시작 및 종료 시 들여쓰기를 맞춰준다. ({, } 기호 등)
- ts=*value* (tabstop) - tab을 눌렀을 때의 간격.
- sw=*value* (shiftwidth) - 블록 단위 간격. 즉 cindent에 영향을 준다.
- tw=*value* (textwidth) - 화면의 너비. 이 값보다 긴 문장은 자동 개행된다. 0이면 disable.
- et (expandtab) - tab대신 space로 변경.
- ff=value (fileformat) - 파일 포맷을 변경할 수 있다. 주로 dos (CR+LF), unix (LF), mac (CR) 을 사용한다.
- fenc=value (fileencoding) - 파일 인코딩을 변경할 수 있다.
  - utf-8, utf8
  - ucs-bom
  - korea : 유닉스에서는 euc-kr, 윈도우즈에서는 cp949로 자동 변환.
  - euc-kr : 유닉스에서만 사용 가능
  - cp949 : 유닉스, 윈도우즈 모두 사용 가능
  - japan : 유닉스에서는 euc-jp, 윈도우즈에서는 cp932로 자동 변환.
  - latin1, ansi : ascii 형식

&nbsp;

## Functions

vim에는 옵션 외에도 설정할 수 있는 기능들이 있다. 옵션이 아니므로 :set 명령을 사용하지 않는다.



많이 사용하는 기능들을 나열하였다.

- :syntax enable - 현재 color scheme으로 문법 체크 기능을 사용한다.
- :syntax on - vim의 기본 설정으로 문법 체크 기능을 사용한다.
- :syntax clear - 문법 체크 기능을 사용하지 않는다. 현재 창에만 적용된다.
- :syntax off - 문법 체크 기능을 사용하지 않는다. 기능을 완전히 중지하고, 모든 버퍼에서 삭제한다.
- :colo[rscheme] {*scheme*} - 해당 색상 테마를 사용한다. 문법 체크 기능과 연동된다.
- :hls[earch] - 검색 시 하이라이팅을 해준다.

&nbsp;

## Setting Files

Unix, Linux, Mac 에서는 **~/.vimrc** 파일로 저장되며, Windows에서는 **~/_vimrc** 파일로 저장된다.

Syntax 파일은 **~/.vim/syntax** 폴더 안에 ***name*.vim** 파일로 저장된다.

특정 파일에만 옵션을 지정하고 싶을 때는 파일의 첫 행에 다음과 같은 방법으로 명시하면 된다.

```vim
/* vim: set ts=2 sw=2: */
```

