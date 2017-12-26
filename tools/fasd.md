---
layout: post
title: fasd
category: tools
tags: [tools, fasd]
---

&nbsp;

# fasd

사용빈도가 높은 파일 또는 디렉토리 검색을 편하게 해준다.

#### Installation

-  MAC

  > $ brew install fasd

- Linux

<<<<<<< Updated upstream
  > $ git clone --depth 1 https://github.com/clvv/fasd ~/.fasd
  > $ cd ~/.fasd
  > $ sudo make install		# install to system-wide
  > \$ PREFIX=\$HOME make install		# install to home
=======
  > $ git clone --depth 1 https://github.com/clvv/fasd ~/.fasd 
  > $ cd ~/.fasd
  > $ sudo make install		# install to system-wide
  > \$ PREFIX=\$HOME make install		# install to home folder
>>>>>>> Stashed changes

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

<<<<<<< Updated upstream
- `a` : any
- `d` : directories
- `f` : files
- `s` : 파일 or 디렉토리 검색
- `z` : 디렉토리 이동

=======
맥에서는 잘 되는데 리눅스에서는 잘 안되고 있다.

- `a` : any
- `f` : files
- `d` : directories
- `s` : show/search/select
- `z` : 디렉토리 이동


#### Reference

- https://github.com/clvv/fasd

>>>>>>> Stashed changes

