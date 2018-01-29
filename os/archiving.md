---
layout: post
title: archiving
category: os
tags: [os, linux, mac, unix]
---



# archiving (압축)

tar는 여러 파일을 하나로 묶어 준다.

`$ tar [function][option] path`

gzip은 하나의 파일을 gz형식으로 압축/해제한다.

`$ gzip [option] filename`

bzip2는 하나의 파일을 bz2 형식으로 압축/해제한다.

`$ bzip2 [option] filename`

### Usage

##### tar

- 압축하기

  `$ tar -cvf <output.tar> <files>`

- 해제하기

  `$ tar -xvf <input.tar>`

##### tar.gz

- 압축하기

  `$ tar -czvf <output.tar.gz> <files>`

  `$ gzip <files>`

- 해제하기

  `$ tar -xzvf <input.tar.gz>`

  `$ gzip -d <input.tar.gz>`

##### tar.bz2

- 압축하기

  `$ tar -cjvf <output.tar.bz2> <files>`

  `$ bzip2 <files>`

- 해제하기

  `$ tar -xjvf <output.tar.bz2> <files>`

  `$ bzip2 -d <output.tar.bz2>`

### Description

##### function

- -c, --create
- -x, --extract, --get

##### option

- -f, --file ARCHIVE
  use archive file or device ARCHIVE
- -j, --bzip2
- -v, --verbose
- -z, --gzip, --gunzip, --ungzip


