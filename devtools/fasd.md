---
layout: post
title: fasd
category: devtools
tags: fasd
---

&nbsp;

# fasd

사용빈도가 높은 파일 또는 디렉토리 검색을 편하게 해준다.

#### Installation

-  MAC

  > $ brew install fasd

- Linux

  > $ git clone --depth 1 https://github.com/clvv/fasd ~/.fasd
  > $ cd ~/.fasd
  > $ sudo make install		# install to system-wide
  > \$ PREFIX=\$HOME make install		# install to home

#### Setting

zsh에 설정을 추가한다. 맥에서는 잘되는 데, 리눅스에선 잘 안된다.

```shell
# .zshrc

plugins=(
	...
	fasd
	...
)
```

#### Usage

- `a` : any
- `d` : directories
- `f` : files
- `s` : 파일 or 디렉토리 검색
- `z` : 디렉토리 이동


