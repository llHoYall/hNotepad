---
layout: post
title: Operation Pending
category: vim
tags: vim
---

&nbsp;

# Operaion Pending

vim에서 일부 명령어는 바로 동작하지 않고 잠시 멈춰서 뒤에 입력되는 명령에 따라 동작을 한다. 모션동작 이라고도 한다.

예를 들어, `d{motion}` 명령의 경우 뒤의 motion 입력에 따라 해당 부분을 삭제한다.

- d$ - 커서 위치부터 라인 끝까지 삭제.
- dd - 현재 라인을 삭제.
- dj - 현재 라인과 아래 라인을 삭제.
- dw - 커서위지부터 단어 끝까지 삭제
- daw - 커서가 위치한 단어를 삭제.
- d} - 커서 위치부터 문단 끝까지 삭제.

&nbsp;

### motion 키

다음은 모션 동작 시에만 사용할 수 있는 명령들이다.

- aw : a word. 공백을 포함하는 한 단어.
- aW : a WORD. 공백을 포함하는 한 단어.
- iw : inner word. 공백을 제외한 한 단어.
- iW : inner WORD. 공백을 제외한 한 단어.

&nbsp;

### motion 명령을 사용하는 명령어

- c{*motion*} : 삭제 후 I-Mode로 전환.
- d{*motion*} : 삭제
- y{*motion*} : 복사

