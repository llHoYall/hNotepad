---
layout: post
title: Abbreviation
category: vim
tags: vim
---

&nbsp;

# Abbreviation

약어 기능으로 I-Mode나 C-Mode에서 alias처럼 사용할 수 있다.

약어를 입력 후 \<SPACE>, \<TAB>, 문장 부호 등을 눌러 독립된 단어로 인식되면 자동으로 변환된다. 독립된 단어로 인식되지 않고 다른 단어 속에 포함된 경우 자동 변환되지 않는다. 이 때 강제로 변환 하려면 **\<CTRL-]>** 키를 누르면 된다. 반대로 독립된 단어로 인식됐지만 자동 변환되지 않기를 원하면 **\<CTRL-v>** 키를 누르면 된다.

약어는 보통 .vimrc 설정파일에 넣어서 사용한다.

설정 파일과 현재 작업 중인 파일의 인코딩 방식이 다르면 작동하지 않으므로, 주의해야한다.

&nbsp;

### 약어 설정

- :ab[breviate] - 현재 설정된 모든 약어 목록을 출력한다.
- :ab[breviate] {*lhs*} - 해당 약어만 출력한다.
- :ab[breviate] {*lhs*} {*rhs*} - lhs를 rhs의 약어로 설정한다.
- :ia[bbrev] {*lhs*} {*rhs*} - I-Mode에서만 동작하는 약어를 설정한다.
- :ca[bbrev] {*lhs*} {*rhs*} - C-Mode에서만 동작하는 약어를 설정한다.

&nbsp;

### 약어 삭제

- :abc[lear] - 모든 약어를 삭제한다.
- :una[bbreviate] {*lhs*} - 해당 약어를 삭제한다.

&nbsp;

### 사용 예

> :ab	mymail	hoya128@gmail.com
>
> :ia	time	\<C-R>=strftime("%Y.%m.%d-%H:%M:%S")\<CR>

I-Mode에서 \<CTRL-r>은 레지스터의 내용을 붙여넣는 명령이다. =는 레지스터의 이름이다. strftime은 내장 크스립트 함수이다.