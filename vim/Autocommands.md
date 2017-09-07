---
layout: post
title: Autocommands
category: vim
tags: vim
---

$~$

# Autocommands

Autocommand는 특정한 이벤트마다 원하는 동작을 자동으로 수행하도록 하는 기능이다.

형식은 다음과 같다.

> :autocmd [group] {events} {file\_pattern} [nested] {command}



예를 들면 다음과 같이 사용한다.

```vim
:function DateInsert()
:	$delete
:	read !date
:endfunction

:autocmd FileWritePre * call DateInsert()
```

위의 내용은 모든 파일의 저장 전에 마지막에 날짜를 붙여라라는 것이다.

$~$

#### group

옵션사항으로 다음의 예와 같이 사용한다.

```vim
:augroup cprograms
:	autocmd BufReadPost *.c,*.h :set sw=4 sts=4
:	autocmd BufReadPose *.cpp :set sw=3 sts=3
:augroup END

# same as

:autocmd cprograms BufReadPost *.c,*.h :set sw=4 sts=4
:autocmd cprograms BufReadPost *.cpp :set sw=3 sts=3
```

$~$

#### events

autocmd를 적용할 이벤트를 나타낸다.

- BufNewFile
- BufReadPost
- Filetype

$~$

#### file\_pattern

autocmd가 적용될 파일들을 나타낸다.

예를 들면, 다음과 같이 사용한다.

- \* - Match any character any number of times
- ? - Match any character once
- [abc] - Match the character a, b, or c
- . - Matches a dot
- a{b,c} - Matches "ab" and "ac"

$~$

#### nested

하나의 이벤트로 다른 이벤트가 유발되는 경우 이를 허용하려면 다음의 예처럼 명시적으로 nested를 붙여준다.

```vim
:autocmd FileChangedShell * neested edit
```

$~$

#### command

autocmd로 실행할 명령을 나타내며, 일반적으로 사용하는 모든 명령이 가능하다.



:execute 명령을 사용하여 이벤트가 발생한 것처럼 다른 autocmd를 실행할 수 있다.

다음의 예를 보자.

```vim
:autocmd BufReadPost *.new execute "doautocmd BufReadPost " . expand("<afile>:r")
```

위 예제는 .new로 끝나는 파일을 편집할 경우, 자동으로 다음 명령을 실행한다.

> :doautocmd BufReadPost {*filename*}.c

:doautocmd 명령은 현재 버퍼를 대상으로 실행하며, :doautoall 명령은 전체 버퍼를 대상으로 실행한다.



:normal 명령을 사용하여 NORMAL 모드 명령어를 사용할 수 있다.

다음의 예를 보자.

```vim
:autocmd BufReadPost *.log normal G
```

위 예제는 .log 파일을 읽은 후, 파일의 가장 마지막으로 이동한다.



:execute 명령을 사용하여 NORMAL 모드 명령어를 사용할 수도 있다.

:normal 명령은 뒤따르는 모든 문자를 명령어로 사용하기 때문에, |등의 다른 명령을 사용할 수 없기 때문에 이런 방법을 사용한다.

다음의 예를 보자.

```vim
:autocmd BufreadPost *.chg execute "normal ONew entry:\<Esc>" |
	\ 1read !date
```

vim script에서는 \기호로 긴 명령어를 분리할 수 있다.

command-line에서는 안된다.

$~$

### Deleting

설정된 autocmd를 삭제하려면 다음의 예처럼 !를 붙인다.

> :autocmd! cprograms
> :autocmd! FileWritePre *

$~$

### Listing

설정된 autocmd 목록을 보려면 다음 명령을 입력한다.

> :autocmd

원하는 그룹 별, 이벤트 별, 설정된 파일별 등으로 목록을 보려면 다음의 예처럼 입력한다.

> :autocmd cprograms
> :autocmd BufNewFile
> :autocmd * \*.c

$~$

### Ignoring Events

이벤트를 무시하고 싶을 땐 'eventignore' 옵션을 이용한다.

다음의 예와 같이 사용할 수 있다.

> :set eventignore=WinEnter,WinLeave>
> :set eventignore=all
> :set eventignore=

$~$

### Reference

- :h autocmd.txt
- :h autocmd-events
- :h restore-position

