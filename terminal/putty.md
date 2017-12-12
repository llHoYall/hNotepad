---
layout: post
title: putty
category: terminal
tags: [terminal, putty]
---

&nbsp;

# putty

### Freezing Issue

`<CTRL-s>`를 누르면 XOFF 상태가 되어 freezing처럼 보인다.

`<CTRL-q>`를 누르면 XON 상태가 된다.

다음의 코드를 추가하면 방지할 수 있다.

```shell
# .bashrc

# Disabling the <CTRL-s> sending XOFF.
stty ixany
stty ixoff -ixon

# Disable only XOFF. You can send <CTRL-s>, <CTRL-q>.
stty stop undef
stty start undef
```

