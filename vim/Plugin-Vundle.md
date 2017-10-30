---
layout: post
title: [Plugin] Vundle
category: vim
tags: vim
---

&nbsp;

# [Plugin] Vundle

Vim의 plugin들을 package manager 처럼 관리할 수 있게 해준다.

&nbsp;

### Installation

Vundle은 git을 사용하여 vim폴더에 설치한다.

> $ git clone https://github.com/VundleVim/Vundle.vim ~/.vim/bundle/Vundle.vim

&nbsp;

### Configuration

**.vimrc** (윈도우즈 에서는 **_vimrc**) 파일에 다음의 설정을 넣는다.

```vim
se		nocp
filet	off
se		rtp+=~/.vim/bundle/Vundle.vim
call	vundle#begin()
Plugin	'VundleVim/Vundle.vim'
Plugin	'vim-airline/vim-airline'
Plugin	'vim-airline/vim-airline-themes'
call	vundle#end()
filet	plugin indent on
```

vim-airline 플러그인은 예시로 넣은 것이다. 이 부분에 각자 원하는 플러그인의 Git URI 주소를 넣으면 된다.

&nbsp;

### Usage

vundle을 사용하여 플러그인을 관리할 수 있다.

1. Install
   vim 상에서 다음의 명령을 입력하거나, command-line 상에서 다음의 명령을 입력하면 vim 설정 파일을 참고하여 플러그인들을 설치한다.
   > :PluginInstall   
   > $ vim +PluginInstall +qall

2. Update
   다음의 명령으로 설치된 플러그인의 업데이트를 할 수 있다.
   > :PluginInstall!
   > :PluginUpdate

3. Search
   다음의 명령으로 (http://vim-scripts.org/vim/scripts.html)에 있는 플러그인을 검색할 수 있다. 
   > :PluginSearch {*name*}

4. List
   다음의 명령으로 설치된 플러그인 목록을 볼 수 있다.
   > :PluginList

5. Clean
   다음의 명령으로 모든 플러그인을 삭제할 수 있다. vim 설정파일에서만 삭제되며 bundle installation directory에는 남아있다.
   > :PluginClean
   > 다음의 명령은 사용되지 않는 플러그인만 삭제한다.
   > :PluginClean!