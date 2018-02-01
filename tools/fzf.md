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

- `<CTRL-t>` : 하위 디렉토리 파일 검색.
- `<CTRL-r>` : 히스토리 검색.
- `<ESC> + c`, `<ALT-c>` : 하위 디렉토리 검색 후 이동.
- `fzf` : 현재 디렉토리를 기준으로 하위 디렉토리 및 파일 검색.
  - Ex) $ fzf --height 30% --reverse
- `fzf-tmux` : tmux의 pane을 분리해서 실행. 
  - -d #: 수평분할
  - -l #: 수직분할
  - Ex) $ git log | fzf-tmux -d 10
  - Ex) $ git log | fzf-tmux -l 30%
- `**` : vim등의 명령어 이후 `**<TAB>`을 입력하면 해당 디렉토리의 파일 검색을 할 수 있다.


