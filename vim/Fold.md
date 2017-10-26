---
layout: post
title: Fold
category: vim
tags: vim
---

&nbsp;

# Fold

### Create

- zf{*motion*} - 모션키 만큼 fold를 생성한다.
- {visual}zf  - 선택된 영역만큼 fold를 생성한다.
- [#]zF - 원하는 만큼의 라인을 fold를 생성한다.
- :{*range*}fo[ld] - 해당 범위만큼 fold를 생성한다.

### Delete

- zd - 커서 위치의 fold 하나를 삭제한다.
- zD - 커서 위치의 fold를 재귀적으로 삭제한다.
- zE - 현재 창의 모든 fold를 삭제한다.

### Open

- zo : 커서 위치의 fold 하나를 펼친다.
- zO : 커서 위치의 fold를 재귀적으로 펼친다.

### Close

- zc : 커서 위치의 fold 하나를 닫는다.
- zC : 커서 위치의 fold를 재귀적으로 닫는다.


&nbsp;

# Reference

- http://vimdoc.sourceforge.net/htmldoc/fold.html

