---
layout: post
title: [VimCasts] #4 Tidying Whitespace
category: vim
tags: vim
---

&nbsp;

# [VimCasts] #4 Tidying Whitespace

### Converting between tabs and spaces

다음 명령은 문서의 \<TAB>과 \<SPACE>를 변경해주는 명령이다.

> :ret[ab]\[!]

\<TAB>  -->  \<SPACE>

> :se et
> :ret!

\<SPACE>  -->  \<TAB>

> :se noet
> :ret!

&nbsp;

### Strip Trailing Whitespace

다음 명령은 문서의 모든 행의 뒤에 붙어있는 의미없는 공백을 지워준다.

> :%s/\s\\+$//e

하지만 2가지 단점이 있다.

- 커서의 위치가 바뀐다.
- 검색 히스토리가 덮어써진다.

그래서 다음과 같은 함수를 만들어 사용한다.

```vim
function! Preserve(command)
	let _s = @/
	let l = line(".")
	let c = col(".")
	execute aLcommand
	let @/ = _s
	call cursor(l, c)
endfunction

nmap _$ :call Preserve("%s/\\s\\+$//e")<CR>
nmap _= :call Preserve("normal gg=G")<CR>
```

&nbsp;

### Delete Blank Lines

다음 명령은 모든 공백 라인을 제거한다.

> g/^$/d

&nbsp;

## Reference

- http://vimcasts.org/episodes/tidying-whitespace
- :h :g[lobal]