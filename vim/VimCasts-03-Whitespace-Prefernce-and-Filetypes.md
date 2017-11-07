---
layout: post
title: [VimCasts] #3 Whitespace Preference and Filetypes
category: vim
tags: vim
---

&nbsp;

# [VimCasts] #3 Whitespace Preference and Filetypes

autocmd를 이용한 자동화 기능으로 특정 파일마다 옵션을 다르게 줄 수 있다.

> 현재 파일의 타입을 알고 싶을 땐 다음 명령을 수행한다. 
>
> :set filetype?
>
> 현재 파일의 타입을 설정하고 싶을 땐 다음 명령을 수행한다.
>
> :setfiletype html

&nbsp;

*.vimrc* 파일에 다음과 같이 원하는 내용을 설정한다.

```vim
if has ('autocmd')
	filet on
	
	autocmd	FileType	html	setl ts=2 sts=2 sw=2 et
	autocmd	FileType	css		setl ts=2 sts=2 sw=2 et
	autocmd	FileType	javascript	setl ts=4 sts=4 sw=4 noet
	
	autocmd	BufNewFile, BufRead	*.rss	setf xml
endif
```

&nbsp;

## Reference

- http://vimcasts.org/episodes/whitespace-preference-and-filetypes
- :help :autocmd
- :help FileType
- :help :setlocal
- :help :setfiletype
- :help BufNewFile
- :help BufRead

