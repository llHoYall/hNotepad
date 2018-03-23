---
layout: post
title: tmuxinator
category: devtools
tags: tmuxinator
---

&nbsp;

# tmuxinator

tmux를 효율적으로 사용할 수 있도록 도와주는 툴이다. 설정 파일을 이용하여 원하는 개발환경을 만들 수 있다.

#### Installation

-  MAC

  > $ brew install ruby
  >
  > $ gem install tmuxinator

- Linux

  > $ sudo apt install ruby
  >
  > $ gem install tmuxinator

#### Setting

zsh에 설정을 추가한다.

```shell
# .zshrc

plugins=(
	...
	tmuxinator
	...
)
```

#### Usage

다음과 같이 새로운 프로젝트를 만든다.

> $ tmuxinator new \<project\>

`~/.config/tmuxinator/<project>.yml` 파일이 생성되고, 자동으로 에디터가 열린다. 설정 파일을 원하는 대로 수정한다.

```yaml
# jekyll 블로그 작성환경 예제
# 1번 window를 2개의 pane으로 수평분할 하여 위쪽은 jekyll 실행, 아래는 ngrok으로 서버 오픈.
# 2번 window에는 post 폴더를 vi로 오픈.

name: project
root: ~/workspace/blah_blah

windows:
	- server:
		layout: main-horizontal
		panes:
			- bundle exec jekyll serve --incremental
			- ngrok http 4000
	- editor: vim _posts
```

이제, 프로젝트를 시작한다.

> $ tmuxinator start \<ptoject\>

