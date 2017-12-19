---
layout: post
title: tig
category: tools
tags: [tools, tig]
---

&nbsp;

# tig

git의 로그를 편하게 볼 수 있게 도와준다.

#### Installation

- MAC

  > $ brew install tig


#### Usage

- `$ git show | tig`
- `$ tig show --pretty=fuller`
- `$ tig --after="May 5th" --before="2017-12-19 10:42"`
- `$ tig tag-1.0..tag-2.0`
- `$ tig origin..HEAD`
- `$ tig tag-2.0 ^tag-1.0`
- `$ tig --since=1.month -n20 -- Documentation/`


#### Reference

- https://github.com/jonas/tig
- https://jonas.github.io/tig/doc/manual.html

