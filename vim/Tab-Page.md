---
layout: post
title: Tab Page
category: vim
tags: vim
---

&nbsp;

# Tab Page

### 탭 페이지 열기

- :[#]tabe[dit] \[*filename*]
  :[#]tabnew [*filename*] - 새 탭 페이지를 연다. 파일을 명시 하지 않으면 빈 문서가 열린다.

&nbsp;

### 탭 페이지 이동 

- [#]gT
  :[#]tabp[revious] - 이전 탭 페이지로 이동한다.
- [#]gt
  :[#]tabn[ext] - 다음 탭 페이지로 이동한다.



- :tabm[ove] \[#] - 현재 탭 페이지를 #번째 탭으로 이동한다. 숫자 생략 시 가장 오른쪽으로 이동한다.

&nbsp;

### 탭 페이지 닫기

- :tabc[lose] - 현재 탭 페이지를 닫는다.
- :tabo[nly] - 현재 탭 페이지를 제외하고 모든 탭 페이지를 닫는다.