---
layout: post
title: File
category: vim
tags: vim
---

&nbsp;

# File

## 열기

- :e[dit] {*filename*} - 명시한 파일을 현재 창에 연다.
- :r[ead] \[*filename*] - 명시한 파일을 읽어 커서 아래쪽에 넣는다. 파일을 명시하지 않을 경우 기본은 현재 파일이다.
- gf - 커서 위치의 파일명을 인식해서 연다.
- \<CTRL-w> f - 커서 위치의 파일명을 인식해서 분할 창에 연다.
- \<CTRL-w> gf - 커서 위치의 파일명을 인식해서 탭 페이지에 연다.

커서 위치의 파일명을 인식할 때, 현재 디렉토리와 path 옵션에 설정된 디렉토리를 순서대로 검색한다. 다음과 같은 방법으로 path 옵션에 디렉토리를 추가할 수도 있다.

> :set path+={*path*}

&nbsp;

## 저장하기

- :w[rite] - 현재 파일명으로 저장한다. 파일명이 없으면 에러가 발생한다. V-Mode에서 사용 가능.
- :w[rite]! - 현재 파일명으로 강제로 저장한다. 파일명이 없으면 에러가 발생한다.
- :w[rite] {*filename*} - 명시한 파일명으로 저장한다.
- :sav[eas] {*filename*} - 현재 파일을 다른 이름으로 저장한다.
- :up[date] - 현재 파일에 변경사항이 있을 때만 저장한다.
- ZZ, :x - 변경사항이 있다면 저장한 후, vim을 종료한다.

