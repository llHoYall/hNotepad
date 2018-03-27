---
layout: post
title: tmux
categories: terminal
tags: [terminal, tmux]
---

&nbsp;

# tmux

screen과 유사한  TTY Multiplexer이다.

&nbsp;

### Installation

- on Mac
  > $ brew install tmux

- on Linux
  > $ sudo apt-get install tmux

&nbsp;

### Setting

설정 파일은 ~/.tmux.conf에 저장한다. 다음을 참고하여 설정을 한다.

- `<CTRL-b> + ?` : 목록 보기
- `<CTRL-b> + :` : 명령어 모드
  - **bind-key [-cnr] \[-t key-table] key command [arguments]** : bind key
  - **unbind-key [-acn] \[t key-table] key** : unbind key
  - **set -g \<*option-name*> \<*option-value*>** : set-option
  - **setw -g \<*option-name*> \<*option-value*>** : set-window-option

##### <u>Working with zsh</u>

```shell
# .zshrc

plugins=(
	...
	tmux
	...
)
```

##### <u>gpakosz/.tmux</u>

다른사람의 설정이다. 이것을 참고하여 개인 설정을 만들수도 있다.

> $ cd
> $ git clone https://github.com/gpakosz/.tmux
> $ ln -s -f .tmux/.tmux.conf
> $ cp .tmux/.tmux.conf.local .

&nbsp;

### Usage

##### <u>Session</u>

- 새 세션 시작
  - `$ tmux new -s <session-name>`
  - `$ tmux new -s <session-name> -n <window-name>` : 윈도우와 함께
- 세션 목록 보기
  - `$ tmux ls`
- 세션 이름 변경
  - `<CTRL-b> + $`
- 세션 중단 (detach)
  - `<CTRL-b> + d`
- 세션 다시 시작 (attach)
  - `$ tmux attach -t <session-name | session-number>`
- 세션 종료
  - `$ exit` : 세션 안에서
  - `$ tmux kill-session -t <session-name>` : 세션 밖에서

##### <u>Window</u>

- 새 윈도우 생성
  - `<CTRL-b> + c`
- 윈도우 이름 변경
  - `<CTRL-b> + ,`
- 포커스 이동
  - `<CTRL-b> + #` : window number
  - `<CTRL-b> + n` : next window
  - `<CTRL-b> + p` : previous window
  - `<CTRL-b> + l` : last window
  - `<CTRL-b> + w` : window selector
  - `<CTRL-b> + f` : find by name
- 윈도우삭제
  - `<CTRL-b> + &`
  - `<CTRL-d>`

##### <u>Pane</u>

- 새 페인 생성
  - `<CTRL-b> + %` : 횡 분할
  - `<CTRL-b> + "` : 종 분할
- 포커스 이동
  - `<CTRL-b> + q + #` : 화면에 각 pane에 해당하는 숫자가 나타난다.
  - `<CTRL-b> + o` : 시계 방향
  - `<CTRL-b> + {` : 왼쪽
  - `<CTRL-b> + }` : 오른쪽
  - `<CTRL-b> + \<ARROW>`
- 크기 변경
  - `<CTRL-b> + :` : 명령어 모드
    - **resize-pane -L #**
    - **resize-pane -R #**
    - **resize-pane -D #**
    - **resize-pane -U #**
- 레이아웃 변경
  - `<CTRL-b> + <SPACE>`
- 줌
  - `<CTRL-b> + z`
- 페인 삭제
  - `<CTRL-b> + x`
  - `<CTRL-d>`


&nbsp;

### Customizing

`$ tmux show-options -g | grep status` : status line 의 현재 설정을 확인한다.

```sh
################################################################################
# Tmux configuration by HoYa
################################################################################

# Easy config reloads
bind r source-file ~/.tmux.conf \; display 'Reload tmux configuration'

# Default-Terminal
set -g default-terminal "screen-256color"

# Create pane
bind  \ split-window -h -c '#{pane_current_path}'
bind  - split-window -v -c '#{pane_current_path}'

# Fast pane switching
#if-shell "uname | grep -q Darwin" "bind -n M-Left select-pane -L; bind -n M-Down select-pane -D; bind -n M-Up select-pane -U; bind -n M-Right select-pane -R;"
#if-shell "uname | grep -q Linux" "bind -n M-h select-pane -L; bind -n M-j select-pane -D; bind -n M-k select-pane -U; bind -n M-l select-pane -R;"
# 위와 같이 OS dependency를 줄 수 있음.
bind -n M-Left select-pane -L
bind -n M-Down select-pane -D
bind -n M-Up select-pane -U
bind -n M-Right select-pane -R

# Pane resizing
bind -nr C-Left resize-pane -L
bind -nr C-Down resize-pane -D
bind -nr C-Up resize-pane -U
bind -nr C-Right resize-pane -R

# Stop renaming windows automatically
set -g allow-rename off

# Escape-Time
set -sg escape-time 10

# Notification
set -g visual-activity on 
set -g visual-bell on
setw -g monitor-activity on

# Status line
set -g status-fg white
set -g status-bg black
set -g status-left-length 30
set -g status-left "#[fg=green,bright] [#S]#[fg=yellow,bright] #(~/.tmux/get-uptime.sh) "
set -g status-right "#[fg=cyan,bright]%H:%M:%S #[fg=magenta,bright]%Y-%m-%d %a "
setw -g window-status-fg blue
setw -g window-status-bg black
setw -g window-status-format " #F[#I]: #W "
setw -g window-status-current-fg black
setw -g window-status-current-bg blue
setw -g window-status-current-format " #F[#I]: #W "
```

