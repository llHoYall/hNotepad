---
layout: post
title: Plugin - Pathogen
category: vim
tags: [vim, plugin]
---

# [Plugin] Pathogen

vim에는 `runtimepath`가 있다. 이것은 어디에서 파일을 로드할지를 알려준다.

pathogen 플러그인은 이 `runtimepath`를 쉽게 관리할 수 있게 해준다.

## Installation

> $ mkdir -p ~/.vim/autoload ~/.vim/bundle
>
> $ curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim

윈도우즈일 경우 ~/.vim을 ~\vimfiles로 바꾼다.

## Runtime Path Manipulation

```vim
# .vimrc
execute pathogen#infect()
syntax on
filetype plugin indent on
```

이제 ~/.vim/bundle 디렉토리 밑에 원하는 플러그인들을 설치한다.

## Customizing

bundle 이라는 디렉토리 이름대신 다른 디렉토리 이름을 쓸 수 있다.

```vim
execute pathogen#infect('stuff/{}')
```

다른 디렉토리 경로를 사용할 수도 있다.

```vim
execute pathogen#infect('bundle/{}', '~/src/vim/bundle/{}')
```

## Package Managing

~/.vim/bundle 디렉토리에서 다음 명령을 사용하면 git의 submodules를 update한다.

> $ git pull origin master

