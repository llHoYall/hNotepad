---
layout: post
title: fzf
category: tools
tags: [tools, fzf]
---

&nbsp;

# fzf

Fuzzy Finder 도구이다.

증분 검색을 통해 원하는 파일이나 히스토리를 쉽고 빠르게 찾을 수 있도록 해준다.

#### Installation

-  MAC

  > $ brew install fzf
  >
  > \# To install useful key bindings and fuzzy completion
  > $ $(brew --prefix)/opt/fzf/install

-  Linux

   > $ git clone --depth 1 https://github.com/junegunn/fzf ~/.fzf
   > $ ~/.fzf/install

-  Windows

   > $ choco install fzf

#### Setting

bash에는 설정이 잘 되는 데, zsh에는 잘 안되는 것 같다. 직접 zsh 설정에 다음 내용을 추가한다.

```shell
# .zshrc

[ -f ~/.fzf.zsh ] && source ~/.fzf.zsh
```

#### Usage

- `<CTRL-t>` : 하위 디렉토리 파일 검색
- `<CTRL-r>` : 히스토리 검색
- `<ESC> + c` : 하위 디렉토리 검색 후 이동

