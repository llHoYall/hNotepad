---
layout: post
title: neovim
category: tools
tags: [tools, neovim]
---

&nbsp;

# fasd

사용빈도가 높은 파일 또는 디렉토리 검색을 편하게 해준다.

#### Installation

-  MAC

  > $ brew install neovim
  >
  > // Fonts
  >
  > $ brew tap caskroom/fonts
  >
  > $ brew cask install font-hack-nerd-font


#### Setting

zsh에 설정을 추가한다.

```shell
# .zshrc

alias vim="nvim"
alias vi="nvim"
alias vimdiff="nvim -d"
export EDITOR=/usr/local/bin/nvim
```

플러그인을 추가하자. 가장 많은 사람들이 사용하는 플러그인을 자동으로 설치해주는 SpaceVim 프로젝트를 이용해보자.

> $ curl -sLf https://spacevim.org/install.sh | bash

테마는 다음과 같이 변경할 수 있다.

```vim
# ~/.SpaceVim.d/init.vim

let g:spacevim_colorscheme = 'onedark'
```

터미널 폰트를 설정한다.

`iTerm2 > Preference > Profiles > Text > Font > Use a different font for non-ASCII text` : Knack Regular Nerd Font Complete

#### Reference

- https://neovim.io/
- https://github.com/ryanoasis/nerd-fonts
- https://github.com/SpaceVim/SpaceVim
- http://spacevim.org/documentation