---
layout: post
title: Vim Script
category: vim
tags: vim
---



# Vim Script

[TOC]

## Introduction

- 설정 내용은 `$MYVIMRC`에 저장을 하면 항상 적용을 할 수 있다.
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

`:set <opt>?` 명령어를 사용하여 설정된 옵션을 확인할 수 있다.

`:echo &<opt>` 명령어를 사용하면 설정된 옵션 값을 확인할 수 있다.

옵션 사이를 공백 문자로 구분하여 여러 옵션을 한 꺼번에 설정하거나 해제할 수 있다.

`:setlocal` 명령어를 사용하여 현재 버퍼에만 적용되는 local 설정을 할 수 있다.



## Key Mapping

`:map <key> <action>` 명령어를 사용하여 키맵핑을 할 수 있다. 해당 키를 누르면 뒤에 있는 <u>**모든 문장**</u>을 실행한다. 즉, 주석을 달아도 모두 실행이 되므로 문제가 될 수 있다.

`:map` 명령어는 Normal, Operator-Pending, Visual 모드에서 사용이 된다. 각각의 모드에서만 동작하도록 하려면 `:nmap`, `:vmap`, `:imap` 등의 명령어를 사용하면 되며, 이는 다른 맵핑에서도 마찬가지다.

`:unmap` 명령어를 사용하여 맵핑 된 키를 해제할 수 있다.

`:noremap` 명령어를 사용하면 재귀적으로 매핑이 일어나는 것을 막을 수 있다. 내가 설정한 매핑이 다른 플러그인 등에 영향을 받아 원하지 않는 동작을 하게될 수도 있으니 항상 이렇게 사용하자.

`:noremap <buffer>` 와 같이 `<buffer>`를 붙이면 해당 buffer에만 적용되는 local 설정이 된다.

Operator-Pending 맵핑을 하게되면, 해당 내용이 실행되기 전에 Visual 모드에서 선택된 영역이 존재하면 해당 범위에 대해 동작하고, 그렇지 않다면 커서의 위치부터 새로운 위치 사이의 범위에 대해 동작한다. `:onoremap in( :<C-u>normal! f(vi(<CR>` 과 같이 `<C-u>` 를 사용하면 Visual 모드에서 선택된 영역이 취소된다. `:normal` 명령어를 사용하면, `<CR>` 과 같은 special character를 해석하지 못한다. 이 때는 `:execute "normal! gg"`와 같이 `:execute` 명령어를 사용한다. `:normal!`과 같이 !를 붙이면 `:nnoremap`과 같은 동작을 한다.



## Leader Key

`:let mapleader=","`로 leader 키를 정의하면 `:nnoremap <leader>d dd`와 같이 키매핑에 사용할 수 있다.

이런 식으로 leader키를 이용하면, 다른 플러그인 등에서 정의한 매핑과 충돌이 발생할 일이 적어지고 언제든 leader 키만 바꿔 모든 개인 매핑을 변경할 수 있게된다.

`:let maplocalleader="-"`와 같이 현재 버퍼에만 적용할 수도 있다.



## Abbreviations

`:iabbrev <lhs> <rhs>` 명령어를 사용하여 약어 설정을 할 수 있다. 

Insert 모드에서 약어 설정된 단어뒤에 non-keyword 문자가 입력되면 자동으로 대체된다. Keyword 문자는 `:set iskeyword?` 명령어로 확인이 가능하다. 보통 다음과 같다.

- 모든 알파벳 대소문자 (악센트 버전 포함).
- 모든 숫자.
- _ (underscore).
- 아스키 문자 192~255.

Mapping은 해당 문자들이 눌리기만 하면 바로 실행이 되지만, Abbreviation은 해당 문자들이 앞뒤의 non-keyword로 분리된 경우에만 실행이 된다.

`:iabbrev <buffer>`와 같이 `<buffer>`를 붙이면 해당 buffer에만 적용되는 local 설정이 된다.



## Autocommands

`:autocmd <event> <pattern> <command> ` 명령어를  사용하여 특정 이벤트마다 자동으로 실행되는 autocommand 설정을 할 수 있다.

- Event는 ','로 구분하여 여러 개를 설정할 수 있다.
  - BufNewFile
  - BufRead
  - BufWritePre
  - FileType \<filetype>
- Pattern은 적용될 파일을 설정한다.
  - *, *.txt, *.html
- Command는 실제 실행될 명령어를 설정한다.

`:augroup` 명령어를 사용하여 group을 지정하여 묶을 수 있다.

```vim
augroup test
	autocmd!
	autocmd BufWrite * :echom "Hello"
	autocmd BufWrite * :echom "World"
augroup END
```

Group 내에서 `autocmd!` 를 실행하면 해당 그룹의 내용을 clear한다.



## Status Lines

`statusline` 옵션을 설정하여 하단바를 꾸밀 수 있다.

```vim
:set statusline=%f
:set statusline+=\ -\ 
:set statusline+=FileType:\ 
:set statusline+=%y
```

위와 같은 형태로 사용을 한다. %fomatter를 사용하여 원하는 내용을 넣는다. 공백 등의 특수 문자는 escape하여 사용한다.

- %f : 파일 경로.
- %F : 파일의 전체 경로.
- %l : 현재 행.
- %L : 전체 행.
- %y : 파일 타입.
- %= : statusline을 분리한다. 즉, 이 formatter 이전은 좌측에, 이후는 우측에 나타난다.

Formatter는 일반적으로 다음의 형태를 따른다.

`%-0{minwid}.{maxwid}{item}`

- \- : 음수는 좌측 정렬, 양수는 우측 정렬.
- 0 : 0을 붙이면 빈칸을 0으로 채워준다.
- minwid : 최소 칸.
- maxwid : 최대 칸
- item : formatter

예를 들면, 다음과 같은 형태로 사용한다.

```vim
:set statusline=%-4l/%04L		" 12  /0079
:set statusline=%4L				"   79
:set statusline=%.20F			" <d/vim/Vim-Script.md
```



## Variables

변수는 아스키문자, 숫자, \_(underscore)로 구성되며, 숫자로 시작할 수 없다.

`:let` 명령어를 사용하면 설정된 변수 목록을 볼 수 있다. 

`:let <variable> = <expression>` 명령어로 변수를 정의할 수 있다. 

변수 부분에 `&<opt>`를 넣으면 옵션에 값을 설정할 수 있다. Vim에서 interger 0은 "false", integer 1은 "true"를 나타낸다.

변수 부분에 `@<reg>`를 넣으면 레지스터의 내용을 설정할 수 있다.

변수의 앞에 붙이는 문자에 따라 의미가 달라진다.

- `b:var` - Local to the current buffer.
- w:var - Local to the current window.
- t:var - Local to the current tab page.
- g:var - global variable (also in a function).
- `l:var` : Local to a function.
- s:var - Local to a :source'ed Vim script.
- `a:var` : Function argument (only inside a function).
- v:var - Global, predefined by Vim.

```vim
" Example
:let test_var = "test"
:let test_var = 17
:echo test_var

:set textwidth=80
:echo &textwidth
:let &textwidth = &textwidth + 10
:set textwidth?
:let &l:number = 1

:let @a = "hello"
```

변수를 해제하려면 `:unlet` 명령어를 사용한다.

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


## Function

함수의 문법은 다음과 같다. 함수의 이름은 대문자로 시작해야한다.

```vim
function <name>(var1, var2, ...)
	<statement>
	[return <statement>]
endfunction
```

명시적으로 `return`을 하지 않으면 `0`을 반환한다.

`:call <func>` 명령어로 함수를 호출한다.

varargs를 사용하려면 다음과 같이 한다.

```vim
function Varg(...)
	echom a:0		" 2 (number of arguments)
	echom a:1		" a (first argument)
	echom a:2		" b (second argument)
	echo a:000		" ['a', 'b'] (list of all varargs)
endfunction
call varg("a", "b")

function Varg2(foo, ...)
	echom a:foo		" a
	echom a:0		" 2
	echom a:1		" b
	echo a:000		" ['b', 'c']
endfunction
call Varg2("a", "b", "c")
```

:function! 명령을 사용하여 이미 존재하는 함수를 재정의 할 수 있다.

:delfunction 명령을 사용하여 함수를 삭제할 수 있다.




## Expressions

표현으로 쓸 수 있는 것은 다음과 같다.

- number
  - 8진수는 0, 16진수는 0x를 숫자 앞에 붙여 표현한다. 8진수 표현 범위를 넘어서면 0을 붙여도 10진수로 처리된다.
  - float는 3.14 혹은 7.68e3과 같이 표현한다.
  - 숫자 끼리의 연산 중 하나라도 실수가 있다면 실수로 처리되고, 정수만 있다면 정수로 처리된다.


- string
  - 문자열 연결은 `.`을 사용한다. 
  - `:echom "Hello "."World"`
  - 문자열이 정수로 시작하지 않는다면, 산술 연산 시 0으로 처리된다.
  - 문자열이 정수로 시작하면, 산술 연산 시 정수로 처리된다.
  - 문자열이 실수로 시작하면, 산술 연산 시 정수부만 처리된다.
  - " (double quote)로 문자열을 감싸면 특수 문자가 처리된다. 원치 않는다면 \ (escape) 해야한다.
  - ' (single quote)로 문자열을 감싸면 문자 그대로 처리된다.
  - `strlen(string)`, `len(string)` 함수로 문자열의 길이를 반환한다.
- variable
- $*NAME* - environment variable
- &*name* - option
- @*r* - register





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



## Dictionary

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

