---
layout: post
title: Vim Script
category: vim
tags: vim
---

$~$

# Vim Script

## Introduction

while loop는 다음과 같이 한다.

~~~vim
while {condition}
	{statements}
endwhile
~~~

\<CTRL-c>를 누르면 강제로 종료할 수 있다.

:echo 명령어를 사용하여 인자 값을 출력할 수 있다.



8, 10, 16진수의 숫자를 사용할 수 있다.

8진수는 숫자0을 앞에 붙여서 표현하고, 16진수는 0x를 앞에 붙여 표현한다.

$~$

## Variable

변수는 아스키문자, 숫자, \_(underscore)로 구성되며, 숫자로 시작할 수 없다.

:let 명령어를 사용하면 설정된 변수 목록을 볼 수 있고, 다음의 문법으로 변수를 정의할 수 있다.

> let {variable} = {expression}

변수의 앞에 붙이는 문자에 따라 의미가 달라진다.

> s:name - variable local to a script file
> b:name - variable local to a buffer
> w:name - variable local to a window
> g:name - global variable (also in a function)
> v:name - variable predefined by Vim

변수를 해제하려면 :unlet 명령어를 사용한다.

변수가 정의되어 있는지 잘 모를 경우 !를 붙이면 정의되어 있지 않더라도 에러가 발생하지 않는다.

~~~vim
let s:count = 1
unlet! s:count
~~~

스크립트가 종료될 때, 변수는 자동으로 해제되지 않는다. 따라서, 이후 다시 스크립트가 실행될 때 원치 않는 오동작이 발생할 수 있으므로 exists() 함수를 사용한 다음의 예처럼 스크립트 시작시 초기화를 해준다.

~~~vim
if !exists("s:count")
	let s:count = 0
endif
let s:count = s:count + 1
echo s:count
~~~

문자열을 변수 값으로 설정할 때는 single quote나 double quote를 사용한다.

Single quote 문자열에서는 single quote를 제외한 모든 문자가 일반 문자로 취급된다.

Double quote 문자열에서는 backslash를 사용한 special 문자를 사용할 수 있다.

- \t - \<Tab>
- \n - \<NL>, line break
- \r - \<CR>, \<Enter>
- \e, \\\<Esc> - \<Esc>
- \b - \<BS>, backspace
- \" - ", double quote
- \\\ - \, backslash
- \\\<C-W> - CTRL-W

$~$

## Reference

- :h usr\_41  (Write a Vim script)

