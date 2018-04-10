---
layout: post
title: vscode - tips and tricks
category: devtools
tags: vscode
---



# Visual Studio Code - Tips and Tricks

## Playground

- `Help -> Interactive Playground`

## Command Palette

- `<⌘⇧p>`, `<F1>`
- `<⌃⇧p>`, `<F1>`

## Quick Open

- `<⌘p>`
- `<⌃p>`

오른쪽 화살표를 누르면 해당 위치의 파일을 연다. 이를 이용해서 여러 파일들을 열 수 있다.

## Go to Symbol

- `<⌃⇧O>` 
- `@:`과 같이 colon을 붙이면 grouping이 된다.

## Command Line

```shell
# open code with current directory
code .

# open the current directory in the most recently used code window
code -r .

# create a new window
code -n

# change the language
code --locale=en

# open diff editor
code --diff <file1> <file2>

# open file at specific line and column <file:line[:character]>
code --goto package.json:10:5

# see help options
code --help

# disable all extensions
code --disable-extensions .
```

