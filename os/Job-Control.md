---
layout: post
title: Job Control
category: os
tags: [os, unix, mac, linux]
---

&nbsp;

# Job Control

다음 명령은 현재 실행중인 작업들을 보여준다.

> $ jobs

현재 실행중인 프로세스에서 \<CTRL-z> 키를 누르면 해당 프로세스를 suspend 한다. 즉, background로 옮겨진다.

다음 명령은 해당 명령어를 background에서 실행한다.

> $ {*cmd*} &

다음 명령은 해당 작업을 foreground/background로 옮긴다.

> $ fg %{*job id*}
>
> $ bg %{*job id*}

다음 명령은 해당 작업을 종료한다.

> $ kill %{*job id*}

