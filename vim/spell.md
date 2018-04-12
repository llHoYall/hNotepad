---
layout: post
title: Spell
category: vim
tags: vim
---

# Spell

Vim에서 스펠링 검사를 하려면 `:set spell` 명령을 사용하여 해당 옵션을 설정한다.

- `]s` : 다음 스펠링 오류로 간다.
- `[s` : 이전 스펠링 오류로 간다.
- `z=` : 스펠링 오류를 자동으로 수정한다.

어떤 언어 사전으로 스펠링 검사를 할 지 명시할 수 있다.

- `:set spelllang=<lang>`
  - `en`, `en_us`, `en_gb`, ...
- `:windo set spelllang=<lang>` : 화면 전체에 해당 언어 사전을 적용한다.
- `:bufdo set spelllang=<lang>` : 현재 버퍼에만 해당 언어 사전을 적용한다.

다음 명령으로 사전을 편집할 수 있다.

- `zg` : 해당 스펠링을 올바른 스펠링으로 사전에 등록한다.
- `zug` : `zg` 명령을 취소한다. 사전에는 주석처리된다.
- `zw` : 해당 스펠링을 잘못된 스펠링으로 사전에 등록한다.
- `zuw` : `zw` 명령을 취소한다. 사전에는 주석처리된다.

`zug`, `zuw` 등의 명령을 사용하면 사전에 주석처리가 되므로 사전 용량이 늘어난다. 이와 같이 사전 내에서 필요 없는 내용을 지우려면 `:runtime spell/cleanadd.vim` 명령을 사용한다. 

사전은 `~/.vim/spell/<language>.<encoding>.add` 와 같이 저장되어 있고, 해당 형식으로 등록할 수 있다. 예를 들면 다음과 같다. `~/.vim/spell/en.utf_8.add`.

