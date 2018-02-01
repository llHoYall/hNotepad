---
layout: post
title: Vim Script
category: vim
tags: vim
---



# Vim Script

## Introduction

- 8, 10, 16진수의 숫자를 사용할 수 있다. 8진수는 숫자0을 앞에 붙여서 표현하고, 16진수는 0x를 앞에 붙여 표현한다.

- Leading 공백 문자는 무시된다.

- 주석은 "(double quote)로 시작한다.

`:sleep` 명령어를 사용하여 잠시 멈출 수 있다.

~~~vim
:sleep 4	" 4 seconds
:sleep 50m	" 50 milliseconds
~~~



## Echoing

`:echo` 명령어를 사용하여 인자 값을 출력할 수 있다.

`:echom` 명령어를 사용하여 인자 값을 출력하고, 메세지 히스토리를 남길 수 있다.

`:messages` 명령어를 사용하여 메세지 히스토리를 볼 수 있다.



## Option

`:set [no]<opt>` 명령어를 사용하여 옵션을 설정하거나 해제할 수 있다.

`:set <opt>=<value>` 명령어를 사용하여 옵션에 값을 설정할 수 있다.

`:set <opt>!` 명령어를 사용하여 옵션을 토글링할 수 있다.

`:set <opt>?` 명령어를 사용하여 설정된 옵션값을 확인할 수 있다.

옵션 사이를 공백 문자로 구분하여 여러 옵션을 한 꺼번에 설정하거나 해제할 수 있다.



## Key Mapping

`:map <key> <action>` 명령어를 사용하여 키맵핑을 할 수 있다. 해당 키를 누르면 뒤에 있는 <u>**모든 문장**</u>을 실행한다. 즉, 주석을 달아도 모두 실행이 되므로 문제가 될 수 있다.

`:map` 명령어는 Normal, Opertion-Pending, Visual 모드에서 사용이 된다. 각각의 모드에서만 동작하도록 하려면 `:nmap`, `:vmap`, `:imap` 등의 명령어를 사용하면 되며, 이는 다른 매핑에서도 마찬가지다.

`:unmap` 명령어를 사용하여 맵핑 된 키를 해제할 수 있다.

`:noremap` 명령어를 사용하면 재귀적으로 매핑이 일어나는 것을 막을 수 있다. 내가 설정한 매핑이 다른 플러그인 등에 영향을 받아 원하지 않는 동작을 하게될 수도 있으니 항상 이렇게 사용하자.



## Variables

변수는 아스키문자, 숫자, \_(underscore)로 구성되며, 숫자로 시작할 수 없다.

`:let` 명령어를 사용하면 설정된 변수 목록을 볼 수 있고, 다음의 문법으로 변수를 정의할 수 있다.

> let {*variable*} = {*expression*}

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

&nbsp;

## Expressions

표현으로 쓸 수 있는 것은 다음과 같다.

- number
- string
- variable
- $*NAME* - environment variable
- &*name* - option
- @*r* - register

String은 다음과 같이 dot로 연결이 가능하다.

~~~vim
echo "Hello" . "World"
~~~

&nbsp;

## Operator

산술 연산

- a + b - add
- a - b - subtract
- a * b - multiply
- a / b - divide
- a % b - modulo



조건 표현

- a ? b : c



논리 연산

- a == b: equal to
- a != b: not equal to
- a > b: greater than
- a >= b: greater than or equal to
- a < b: less than
- a <= b: less than or equal to



문자열 연산

- a =~ b: matches with
- a !~ b: does not match with

&nbsp;

## Flow Control

if 조건문의 문법은 다음과 같다.

> if {*condition*}
> ​	{*statements*}
> elseif {*condition*}
> ​	{*statements*}
> else
> ​	{*statements*}
> endif



for loop의 문법은 다음과 같다.

> for {*varname*} in {*listexpression*}
> ​	{*statements*}
> endfor



while loop의 문법은 다음과 같다.

> while {*condition*}
> ​	{*statement*s}
> ​	[continue]	" jump back to the start of the while loop; the loop continues
> ​	[break]		" jump forward to the :endwhile; the loop is discontinued
> endwhile

\<CTRL-c>를 누르면 강제로 종료할 수 있다.

&nbsp;

## Function

함수의 문법은 다음과 같다.

> function {*name*}({*var1*}, {*var2*}, ...)
> ​	{*statement*s}
> ​	[return] {*statement*}
> endfunction

:call 명령어로 함수를 호출할 수 있다.

:function! 명령을 사용하여 이미 존재하는 함수를 재정의 할 수 있다.

:delfunction 명령을 사용하여 함수를 삭제할 수 있다.

&nbsp;

## List and Dictionary

List는 square bracket과 comma로 만들어지며 다음의 문법을 따른다.

> [item1, item2, item3, ...]

Plus 연산자로 리스트를 연결할 수 있다.

> list1 + list2

extend 함수로 확장할 수 있다.

> :call extend(list1, list2)

add 함수로 중첩시킬 수 있다.

> :call add(list1, list2)

sort 함수로 정렬할 수 있다.



Dictionary는 curly brace안에 key와 value로 만들어지며 다음의 문법을 따른다.

> {\<key1>:  \<value1>,  \<key2>: \<value2>, ...}

keys 함수로 키들을 list로 뽑을 수 있다.

key를 인덱스로 value를 뽑을 수 있다.

> dict[key]
> dict.key

이미 있는 dictionary에 새로운 키-값 쌍을 추가할 수 있다.

> dict.new\_key =  new\_value

Dictionary에 함수를 넣을 수도 있다.

> function dict.key(*parameters*) dict
> ​	{*statements*}
> endfunction

&nbsp;

## Exception

예외 처리는 다음의 문법과 같다.

> try
> ​	{*expression*}
> catch {*errorcode*}
> ​	{*statements*}
> finally
> ​	{*statements*}
> endtry

&nbsp;

## Reference

- :h usr\_41  (Write a Vim script)

