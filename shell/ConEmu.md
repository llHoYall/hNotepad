---
layout: post
title: ConEmu
category: shell
tags: [shell, conemu]
---

&nbsp;

# ConEmu

Windows에서 사용할 수 있는 Console Emulator이다.

> https://conemu.github.io/

&nbsp;

### Installation

> $ choco install ConEmu -y

&nbsp;

### Setting

설정 파일의 위치를 지정할 수 있다. 난 다음의 경로를 사용한다.

> C:\Users\Account\AppData\Roaming\ConEmu.xml

실행 중에는 `<WIN> + <ALT> + p` 키를 누르면 설정 창이 열린다.

&nbsp;

### Usage

#### Tab 기능

- `<WIN> + n` : 새로운 콘솔 다이얼로그를 보여준다.
- `<WIN> + x` : 새로운 cmd 콘솔을 연다.
- `<WIN> + w` : 새로운 powershell 콘솔을 연다.
- `<WIN> + s` : 새로운 powershell 콘솔을 현재 탭의 root process를 복제하여 연다. 즉 관리자 모드면 관리자 모드로, 일반 모드면 일반 모드로 연다.
- `<WIN> + <DELETE>` : 현재 탭 혹은 창을 닫는다.
- `<CTRL> + <TAB>`, `<WIN> + q` : 다음 탭으로 이동한다.
- `<CTRL> + <SHIFT> + <TAB>`, `<WIN> + <SHIFT> + q` : 이전 탭으로 이동한다.
- `<CTRL> + <NUM>` : 해당 탭으로 이동한다.

#### 화면 분할 기능

- `<CTRL> + <SHIFT> + o` : 수평 분할 창을 연다.
- `<CTRL> + <SHIFT> + e` : 수직 분할 창을 연다.

### 화면 제어 기능

- `<CTRL> + <WIN> + <ENTER>` : 창을 최대로 늘린다. 다시 누르면 Toggle 된다.
- `<CTRL> + <ARROW>` : 현재 창을 스크롤 한다.