---
layout: post
title: Tips and Tricks
category: git
tags: git
---

# Tips and Tricks

## 과거의 커밋에서 특정 파일을 삭제

> $ git filter-branch --index-filter	\
>
> ​	'git rm --cached --ignore-unmatch <files>'	\
>
> ​	--tag-name-filter cat -- --all

