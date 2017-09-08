---
layout: post
title: [VimCasts] #1 Show Invisible
category: vim
tags: vim
---

$~$

# [VimCasts] #1 Show Invisibles

숨겨진 문자를 표시하는 방법을 설명한다.

> N 모드에서  <\l>키를 누르면 tab과, eol이 각각 지정한 문자로 보인다.



*.vimrc* 파일에 다음의 내용을 추가한다.

 ~~~vim
" .vimrc
nmap <leader>| :set list!<CR>
set listchars=tab:▸\, eol:¬
 ~~~

- \<leader>는 backslash키를 의미한다.
- l은 L의 영어 소문자 이다.
- ▸ 기호는 유니코드 \<u25b8> black right-pointing small triangle 이다.
- ¬기호는 유니코드 \<u00ac> not sign 이다.



위 문자를 원하는 색상으로 변경할 수도 있다. 다음의 코드를 colorscheme 파일에 추가한다.

~~~vim
" colorscheme file
highlight NonText guifg=#4a4a59
highlight SpecialKey guifg=#4a4a59
~~~

$~$

## Reference

- :help 'list'
- :help listchars
- :help hl-NonText
- :help hl-SpecialKey
- :help i\_CTRL-V\_digit

