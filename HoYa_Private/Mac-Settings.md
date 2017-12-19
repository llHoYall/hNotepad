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

- **neovim**
  https://neovim.io/

- **fzf**
  https://github.com/junegunn/fzf

- **fasd**
  https://github.com/clvv/fasd

- **tig**
  https://github.com/jonas/tig



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

- **tmux**

