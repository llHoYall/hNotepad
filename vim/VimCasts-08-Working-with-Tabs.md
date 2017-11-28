---
layout: post
title: [VimCasts] #8 Working with Tabs
category: vim
tags: vim
---

&nbsp;

# [VimCasts] #8 Working with Tabs

탭 기능을 사용해보자.

탭을 만들려면 다음 명령어를 사용한다.

- **:tabe[dit] \[*filename*]**  - Open filename in a new tab
- **\<CTRL-w> t** - Move current split window into its own tab

탭을 닫으려면 다음 명령어를 사용한다.&nbsp;

- **:q** - Close window, closing tab if it contains a single window
- **:tabc[lose]** - Close the current tab page and all its windows
- **:tabo[nly]** - Close all tabs apart from the current oner

탭 간에 포커스를 변경하려면 다음 명령어를 사용한다.

- **gt** - Move to next tab
- **gT** - Move to previous tab
- **\#gt** - Move to tab number #

탭의 위치를 변경하려면 다음 명령어를 사용한다.

- **:tabm[ove]** - Move current tab to the end
- **:tabm[ove] #** - Move current tab page to after tab page #. Use zero to make the current tab page the first one.

&nbsp;

### Reference

- http://vimcasts.org/episodes/working-with-tabs

