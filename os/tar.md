---
layout: post
title: tar
category: os
tags: [os, linux, mac, unix]
---



# tar

압축을 하거나 해제할 때 사용하는 명령어이다.

`$ tar [function][option] path`

### Usage

##### tar

- 압축하기

  `$ tar -cvf <output.tar> <files>`

- 해제하기

  `$ tar -xvf <input.tar>`

##### tar.gz

- 압축하기
  `$ tar -zcvf <output.tar.gz> <files>`

- 해제하기

  `$ tar -zxvf <input.tar.gz>`

### Description

##### function

- -c, --create
- -x, --extract, --get

##### option

- -f, --file ARCHIVE
  use archive file or device ARCHIVE
- -j, --bzip2
- -v, --verbose

