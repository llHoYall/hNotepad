---
layout: post
title: MAC - Settings
category: MAC
tags: [MAC,OSX]
---

&nbsp;

# MAC - Settings

## System

### System Preferences

##### Trackpad

- Point & Click
  - Tap to click

##### Accessibility

- Mouse & Trackpad
  - Trackpad options...
    - Enable dragging: three finger drag

&nbsp;

## Finder

### Finder Preferences

##### General

- New Finder windows show: \<home\>

##### Advanced

- Show all filename extensions

### Downloads folder

##### View -> Show View Options (⌘ + J)

- Arrange By: Date Added

&nbsp;

## Applications

### Xcode (command line tools 설치)

> $ xcode-select --install

### Homebrew (MAC용 패키지 관리자)

> \$ /usr/bin/ruby -e "\$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
>
> $ brew doctor

### Git

> $ brew install git git-lfs

git-lfs는 large file storage로 용량이 큰 바이너리 파일을 git으로 관리할 때 유용하다.

### Neovim

##### Installation

> $ brew install neovim
>
> $ brew tap caskroom/fonts
>
> $ brew cask install font-hack-nerd-font

##### Setting

~/.zshrc에 neovim 설정을 추가한다.

```shell
alias vim="nvim"
alias vi="nvim"
alias vimdiff="nvim -d"

export EDITOR=/usr/local/bin/nvim
```

iTerm2에 폰트를 설정한다.

`Preferences -> Profiles -> Text -> Font -> Use a different font for non-ASCII text: Knack Regular Nerd Font Complete`

Plugin

> $ curl -sLf https://spacevim.org/install.sh | bash

최초 실행 시 모드 설정을 물어본다. 1을 누르면 자동으로 플러그인을 설치한다.

### fzf

fuzzy finder 도구이다. 증분 검색을 통하여 원하는 파일이나 히스토리를 쉽고 빠르게 찾을 수 있게 해준다.

##### Installation

> $ brew install fzf
>
> $ $(brew --prefix)/opt/fzf/install

##### Usage

- `^ + t` : 하위 디렉토리 파일 검색
- `^ + r` : 히스토리 검색
- `<ESC> + c` : 하위 디렉토리 검색 후 이동

### fasd

사용빈도가 높은 파일 또는 디렉토리 검색을 편하게 해준다.

##### Installation

> $ brew install fasd

##### Setting

~/.zshrc에 plugin을 추가한다.

```shell
plugins=(
	...
	fasd
	...
)
```

##### Usage

- `z` : 디렉토리 이동
- `s` : 파일 or 디렉토리 검색

단축키를 누르고 \<TAB\> 자동 완성을 통해 명령어 입력 시 언제나 사용할 수 있다. 심지어 다른 명령어 중간에서도 사용 가능하다.

&nbsp;

## Terminal & Shell

### iTerm2

##### Installation

> $ brew cask install iterm2

brew는 소스 코드를 직접 빌드하는 방법을 사용하고, brew cask는 바이너리를 직접 받아서 설치하고 필요한 설정들을 자동으로 세팅한다.

http://iterm2colorschemes.com에서 테마를 다운받을 수 있다.

- obsidian
- solarized dark
- wombat

##### Setting

Preferences -> Profiles -> Colors -> Color Presets...
### Zsh & oh-my-zsh

##### Installation

> $ brew install zsh zsh-completions
> \$ sh -c "\$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
> \$ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
> \$ git clone git://github.com/zsh-users/zsh-autosuggestions \$ZSH_CUSTOM/plugins/zsh-autosuggestions

##### Setting

~/.zshrc 파일에 다음의 설정을 추가한다.

```shell
plugins=(
  git
  zsh-syntax-highlighting
  zsh-autosuggestions
)
```

### tmux
