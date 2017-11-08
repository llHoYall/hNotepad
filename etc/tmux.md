---
layout: post
title: tmux
categories: [unix, mac]
tags: [unix, mac, tool, tmux]
---

&nbsp;

# tmux

screen과 유사한  TTY Multiplexer이다.

&nbsp;

#### Installation

- on Mac

  > $ brew install tmux

- on Linux

  > $ sudo apt-get install tmux

&nbsp;

#### Using

- Session

  > \# 시작
  > **$ tmux new -s \<*session-name*>**
  >
  > \# 윈도우와 함께 시작
  > **$ tmux new -s \<*session-name*> -n \<*window-name*>**
  >
  > \# 목록 보기
  > **$ tmux ls**
  >
  > \# 이름 변경
  > **\<CTRL-b> + $**
  >
  > \# 중단 (Detached)
  > **\<CTRL-b> + d**
  >
  > \# 다시 시작
  > **$ tmux attach -t \<*session-name* | *session-number*>**
  >
  > \# 종료 (세션 내에서)
  > **exit**
  >
  > \# 종료 (세션 밖에서)
  > **$ tmux kill-session -t \<*session-name*>**

- Window

  > \# 생성
  > **\<CTRL-b> + c**
  >
  > \# 이름 변경
  > **\<CTRL-b> + ,**
  >
  > \# 포커스 이동
  > **\<CTRL-b> + #** : window number
  > **\<CTRL-b> + n** : next window
  > **\<CTRL-b> + p** : previous window
  > **\<CTRL-b> + l** : last window
  > **\<CTRL-b> + w** : window selector
  > **\<CTRL-b> + f** : find by name
  >
  > \# 삭제
  > **\<CTRL-b> + &**
  > **\<CTRL-d>**

- Pane

  > \# 횡 분할
  > **\<CTRL-b> + %**
  >
  > \# 종 분할
  > **\<CTRL-b> + "**
  >
  > \# 포커스 이동
  > **\<CTRL-b> + q + #** : 화면에 각 pane에 해당하는 숫자가 나타난다.
  > **\<CTRL-b> + o** : 시계 방향
  > **\<CTRL-b> + {** : 왼쪽
  > **\<CTRL-b> + }** : 오른쪽
  > **\<CTRL-b> + \<ARROW>**
  >
  > \# 크기 변경
  > **\<CTRL-b> + :** : 명령어 모드
  > ​	**resize-pane -L #**
  > ​	**resize-pane -R #**
  > ​	**resize-pane -D #**
  > ​	**resize-pane -U #**
  >
  > \# 레이아웃 변경
  > **\<CTRL-b> + \<SPACE>**
  >
  > \# Zoom
  > **\<CTRL-b> + z**
  >
  > \# 삭제
  > **\<CTRL-b> + x**
  > **\<CTRL-d>**

&nbsp;

#### Setting

설정 파일은 ~/.tmux.conf에 저장 합니다.

- Shortcut

  > \# 목록 보기
  > **\<CTRL-b> + ?**
  >
  > \# Bind & Unbind
  > **\<CTRL-b> + :**
  > ​	**bind-key [-cnr] \[-t key-table] key command [arguments]**
  > ​	**unbind-key [-acn] \[t key-table] key**

- Option

  > \# set-option
  > **\<CTRL-b> + :**
  > ​	**set -g \<*option-name*> \<*option-value*>**
  >
  > \# set-window-option
  > **\<CTRL-b> + :**
  > ​	**setw -g \<*option-name*> \<*option-value*>**

