---
layout: post
title: [VimCasts] #5 Indentation Commands
category: vim
tags: vim
---

&nbsp;

# [VimCasts] #5 Indentation Commands

들여쓰기를 정렬을 하는 방법이다. '<', '>', '=' 명령을 사용한다.

- [#]<< - Shift [#] lines one 'shiftwidth' leftwards.
- <{*motion*} - Shift {*motion*} lines one 'shiftwidth' leftwards.
- :[*range*]< - Shift [*range*] lines one 'shiftwidth' left. Repeat '<' for shifting multiple 'shiftwidth's.
- {*visual*}[#]< - Shift the highlighted lines [#] 'shiftwidth' leftwards.
- [#]>> - Shift [#] lines one 'shiftwidth' rightwards.
- \>{*motion*} - Shift {*motion*} lines one 'shiftwidth' rightwards.
- :[*range*]> - Shift [*range*] lines one 'shiftwidth' right. Repeat '<' for shifting multiple 'shiftwidth's.
- {*visual*}[#]> - Shift the highlighted lines [#] 'shiftwidth' rightwards.
- ={*motion*} - {*motion*} 만큼 들여쓰기를 정렬한다.
- [#]== - #만큼의 라인의 들여쓰기를 정렬한다.
- {*visual*}= - V-Mode에서 선택한 영역의 들여쓰기를 정렬한다.

&nbsp;

## Reference

- http://vimcasts.org/episodes/indentation-commands
- :h shift-left-right
- :h =
- :h text-objects