---
layout: post
title: Cursor Motion
category: vim
tags: vim
---

&nbsp;

# Cursor Motion

## Cursor Motion

- [#]h : 입력한 숫자만큼 왼쪽으로 이동. h만 입력 시 한 칸이동.
- [#]j : 입력한 숫자만큼 아래쪽으로 이동. j만 입력 시 한 칸이동.
- [#]k : 입력한 숫자만큼 위쪽으로 이동. k만 입력 시 한 칸이동.
- [#]l : 입력한 숫자만큼 오른쪽으로 이동. l만 입력 시 한 칸이동.




- [#]w : 단어의 시작 혹은 문장 부호 (., ?, / 등)의 경계를 따라 이동.
- [#]W : 단어가 가진 의미를 따져서 이동.
- [#]b : w와 같지만 역방향으로 이동.
- [#]B : W와 같지만 역방향으로 이동.
- [#]e : 단어의 끝 혹은 문장 부호의 경계를 따라 이동.
- [#]E : 단어가 가진 의미를 따져서 이동.
- [#]ge : e와 같지만 역방향으로 이동.
- [#]gE : E와 같지만 역방향으로 이동.




- 0 : 첫번째 문자로 이동. 공백 문자도 문자이다.
- ^ : 공백을 제외한 라인의 맨 앞으로 이동.
- $ : 라인의 맨 끝으로 이동.
- [#]gg : #번째 라인으로 이동. 생략 시 첫 라인. V-Mode에서 사용 가능.
- [#]G : #번째 라인으로 이동. 생략 시 마지막 라인. V-Mode에서 사용 가능.
- :# : #번째 라인으로 이동.




- '', \`\` : To the position before the latest jump, or where the last "m'" or "m`" command was given.
- '", `" : To the cursor position when last exiting the current buffer.
- '. : To the position where the last change was made.




- H : 현재 화면에서 가장 위 라인의 공백이 아닌 첫 글자로 이동.
- M : 현재 화면에서 중간 라인의 공백이 아닌 첫 글자로 이동.
- L : 현재 화면에서 가장 아래 라인의 공백이 아닌 첫 글자로 이동.




- % : 괄호 짝으로 이동.
- (, ) : 문장 (sentence) 단위의 시작, 끝 위치로 이동.
- {, } : 문단 (paragraph) 단위의 시작, 끝 위치로 이동.
- [[ : Sections backward or to the previous '{' in the first column.
- [] : Sections backward or to the previous '}' in the first column.
- ]] : Sections forward or to the next '{' in the first column.
- ][ : Sections forward or to the next '}' in the first column.

&nbsp;

## Scroll

- \<CTRL-b> : 위로 한 화면 스크롤.
- \<CTRL-f> : 아래로 한 화면 스크롤.
- \<CTRL-u> : 위로 반 화면 스크롤.
- \<CTRL-d> : 아래로 반 화면 스크롤.

&nbsp;

## Information

- \<CTRL-g> : 현재 커서위치의 정보를 표시.


