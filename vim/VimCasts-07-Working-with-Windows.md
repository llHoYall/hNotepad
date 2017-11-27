---
layout: post
title: [VimCasts] #7 Working with Windows
category: vim
tags: vim
---

&nbsp;

# [VimCasts] #7 Working with Windows

윈도우 기능을 사용해보자.

분할 윈도우를 열려면 다음 명령어를 사용한다.

- **\<CTRL-w> s** - split the current window horizontally, loading the same file in the new window
- **\<CTRL-w> v** - split the current window vertically, loading the same file in the new window
- **:sp**[lit] **\<*filename*>** - split the current window horizontally, loading *filename* in the new window
- **:vsp**[lit] **\<*filename*>** - split the current window vertically, loading *filename* in the new window


분할 윈도우를 닫으려면 다음 명령어를 사용한다.

- **:q**[uit] - close the currently active window
- **:on**[ly] - close all windows except the currently active window

분할 윈도우 간에 포커스를 바꾸려면 다음 명령어를 사용한다.

- **\<CTRL-w> w** - cycle between the open windows
- **\<CTRL-w> h** - focus the window to the left
- **\<CTRL-w> j** - focus the window to the down
- **\<CTRL-w> k** - focus the window to the up
- **\<CTRL-w> l** - focus the window to the right

분할 윈도우의 크기를 변경하려면 다음 명령어를 사용한다.

- **\<CTRL-w> +** - increase height of current window by 1 line
- **\<CTRL-w> -** - decrease height of current window by 1 line
- **\<CTRL-w> _** - maximize height of current window
- **\<CTRL-w> |** - maximize width of current window

분할 윈도우의 위치를 변경하려면 다음 명령어를 사용한다.

- **\<CTRL-w> r** - rotate all windows
- **\<CTRL-w> x** - exchange current window with its neighbor
- **\<CTRL-w> H** - move current window to far left
- **\<CTRL-w> J** - move current window to bottom
- **\<CTRL-w> K** - move current window to top
- **\<CTRL-w> L** - move current window to far right

&nbsp;

### Reference

- http://vimcasts.org/episodes/working-with-windows


