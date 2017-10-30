---
layout: post
title: [VimCasts] #2 Tabs and Spaces
category: vim
tags: vim
---

&nbsp;

# [VimCasts] #2 Tabs and Spaces

\<TAB>과 \<SPACE> 설정에 대한 방법을 설명한다.

- 'tabstop'
  \<TAB> 키를 누르면 설정된 간격만큼 공백이 있는 것처럼 띄어져 보인다.
  실제로는 \<TAB> 키 하나이다.
- 'softtabstop'
  \<TAB> 키나 \<BS> 키를 누를 때, 설정된 간격만큼 적용이 된다.
  'tabstop'보다 작게 설정이 되어 있다면, 설정된 개수만큼 \<SPACE>가 입력되고, \<TAB> 키를 여러번 눌러 'tabstop'과 같은 간격이 되면 \<TAB>으로 변한다.
- 'shiftwidth'
  'cindent' 옵션이나 >>, << 명령 등에 적용이 된다. 즉, indent step이다.
- 'expandtab'
  \<TAB> 키를 누르면 설정된 개수만큼 \<SPACE>가 입력된다.

&nbsp;

> **\<TAB>**을 선호하면 **tabstop= == softtabstop**과 같이 설정하는 편이 좋다.
> **\<SPACE>**를 선호하면 **softtabstop == shiftwidth**와 같이 설정하는 편이 좋다.

&nbsp;
*.vimrc* 파일에 다음과 같은 방식으로 원하는 값을 설정한다.
```vim
" .vimrc
se	ts=2
se	sts=2
se	sw=2
se	noet
```

&nbsp;

## Reference

- http://vimcasts.org/episodes/tabs-and-spaces
- :help tabstop
- :help softtabstop
- :help shiftwidth
- :help expandtab

