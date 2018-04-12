---
layout: post
title: VimScript - Plugin Layout
category: vim
tags: [vim, plugin]
---

# VimScript - Plugin Layout

- `~/.vim/colors/` : color scheme.
- `~/.vim/plugin/` : Vim이 시작될 때마다 1번 실행된다.
- `~/.vim/ftdetect/` : Vim을 실행시킬 때마다 실행된다.
- `~/.vim/ftplugin/` : 이 폴더에 직접 플러그인을 넣어도 되고, 기능별로 분리한 플러그인들을 서브 폴더로 넣어도 된다.
  - :set filetype=lang
  - ~/.vim/ftplugin/lang.vim
  - ~/.vim/ftplugin/lang/*.vim
- `~/.vim/indent/` : vim 파일의 이름에 의해 로딩된다.
- `~/.vim/compiler/` : vim 파일의 이름에 의해 로딩된다.
- `~/.vim/after/` : Vim이 시작될 때마다 `~/.vim/plugin/` 실행 이후에 실행된다.
- `~/.vim/autoload/` : 플러그인이 실제로 필요할 때까지 로딩을 연기한다.
- `~/.vim/doc/` : `:help` 명령으로 실행할 수 있다.


