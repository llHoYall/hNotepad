---
layout: post
title: Colorscheme
category: vim
tags: vim
---

&nbsp;

# Colorscheme

원하는 색조합으로 vim을 꾸미는 방법이다.

다음 명령어는 하이라이팅을 설정할 수 있다.

- **:hi[ghlight]** - 현재 설정된 그룹별 하이라이트 설정을 보여준다.
- **:hi[ghlight]** {*group*} - 해당 그룹의 하이라이트 설정을 보여준다.
- **:hi[ghlight]** clear - 현재 설정된 모든 하이라이트를 리셋한다.
- **:hi[ghlight]** clear {*group*} - 해당 그룹의 하이라이트 설정을 disable한다.
- **:hi[ghlight]** {*group*} {*key*}={*arg*} ... - 해당 그룹의 하이라이트 설정을 한다.

다음 명령어는 그룹에 해당하는 내용을 설정할 수 있다.

- **:mat[ch]** {*group*} /{*pattern*}/ - 설정된 패턴에 맞는 내용을 원하는 그룹으로 설정한다. 설정은 여러개를 동시에 할 수도 있다.

&nbsp;

## Group

- Comment : 주석

지정되어 있는 group 외에도 다음의 예처럼 직접 임의의 이름을 지정할 수도 있다.

```vim
hi	myGroup	ctermbg=DarkBlue
```

&nbsp;

## Key

### Color Terminals

- **ctermfg**={*color*}
- **ctermbg**={*color*}

#### **< cterm-colors table >**

| NR-16 | NR-8 | Color Name                       |
| ----- | ---- | -------------------------------- |
| 0     | 0    | Black                            |
| 1     | 4    | DarkBlue                         |
| 2     | 2    | DarkGreen                        |
| 3     | 6    | DarkCyan                         |
| 4     | 1    | DarkRed                          |
| 5     | 5    | DarkMagenta                      |
| 6     | 3    | Brown, DarkYellow                |
| 7     | 7    | LightGray, LightGrey, Gray, Grey |
| 8     | 0*   | DarkGray, DarkGrey               |
| 9     | 4*   | Blue, LightBlue                  |
| 10    | 2*   | Green, LightGreen                |
| 11    | 6*   | Cyan, LightCyan                  |
| 12    | 1*   | Red, LightRed                    |
| 13    | 5*   | Magenta, LightMagenta            |
| 14    | 3*   | Yellow, LightYellow              |
| 15    | 7*   | White                            |

Color name은 대소문자를 구분하지 않는다.

*가 붙은 것은 8-color terminal에서 bold로 표시된다.

### GUI

- **guifg**={*color*}
- **guibg**={*color*}

GUI color name은 색상명을 직접 입력하거나 hex값을 사용해도 된다.

> :hi Comment guifg=SeaGreen guibg=#11f0c3