---
layout: post
title: Key Mapping
category: vim
tags: vim
---

$~$

# Key Mapping

### key mapping

Vim은 key mapping을 통하여 원하는 동작을 단축키로 설정할 수 있다.

예를 들면 다음과 같다.

~~~vim
:map <F2> GoDate: <Esc>:read !date<CR>kJ
" N, V, O 모드에서 <F2> 키를 누르면 문서의 마지막에 현재 date를 입력한다.

:imap <F2> <CR>Date: <Esc>:read !date<CR>kJ
" I 모드에서 <F2> 키를 누르면 문서의 마지막에 현재 date를 입력한다.
~~~



각 모드별 key mapping 설정을 위한 명령어는 다음과 같다.

- :map {lhs} {rhs} - Normal, Visual, Operator-pending
- :vm[ap] {lhs} {rhs} - Visual
- :nm[ap] {lhs} {rhs} - Normal
- :om[ap] {lhs} {rhs} - Operator-pending
- :map! {lhs} {rhs} - Insert, Command-line
- :im[ap] {lhs} {rhs} - Insert
- :cm[ap] {lhs} {rhs} - Command-line

또, :map과 같이 인자없이 명령어만 입력할 경우 현재 정의된 key mapping 목록을 볼 수 있다.

$~$

### remapping

Vim의 key mapping은 remapping이 가능하다. 그렇기 때문에 기본적으로 recursive하다. 다음의 예를 보자.

~~~vim
:map ,, :s/old/new/<CR>:wnext<CR>,,
" 열려진 목록을 순회하면서 old문자열을 new문자열로 바꾼다.
" ,,이 다시 remapping 되므로 오류가 발생할 때까지 순회한다.
~~~

이를 이용하여 처음의 예를 다음과 같이 설정할 수 있다.

~~~vim
:map <F2> G<F3>
:imap <F2> <Esc><F3>
:map <F3>oDate: <Esc>:read !date<CR>kJ
" <F3>가 자동으로 확장되어 <F2>가 remapping 된다.
~~~

이러한 remapping을 막으려면 다음 명령으로 설정을 한다.

- :no[remap] {lhs} {rhs}
- :vn[oremap] {lhs} {rhs}
- :nn[oremap] {lhs} {rhs}
- :ono[remap] {lhs} {rhs}
- :no[remap]! {lhs} {rhs}
- :ino[remap] {lhs} {rhs}
- :cno[remap] {lhs} {rhs}

$~$

### unmapping

설정된 key mapping을 삭제하려면 다음 명령을 사용한다.

- :unm[ap] {lhs}
- :vu[nmap] {lhs}
- :nun[map] {lhs}
- :ou[nmap] {lhs}
- :unm[ap]! {lhs}
- :iu[nmap] {lhs}
- :cu[nmap] {lhs}

각 모드별 설정을 모두 삭제하려면 다음 명령을 사용한다.

- :mapc[lear]
- :vmapc[lear]
- :nmapc[lear]
- :omapc[lear]
- :mapc[lear]
- :imapc[lear]
- :cmapc[lear]

$~$

### Key mapping vs Abbreviation

Abbreviation은 mapping된 key를 입력하고 non-word character를 입력하면 trigger되고, key mapping은 mapping된 key의 마지막 글자를 입력하면 trigger된다.



Abbreviation은 입력 도중 실수해도 수정을 할 수 있고, key mapping은 불가능하다.

$~$

### Reference

- :h usr\_40  (|40.1| - Key Mapping)
- :h map.txt
- :h map-\<script>
- :h map-\<buffer>
- :h map-\<unique>


