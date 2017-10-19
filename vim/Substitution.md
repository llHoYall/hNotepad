---
layout: post
title: Substitution
category: vim
tags: vim
---

&nbsp;

# Substitution

문자열 교체는 C-Mode에서 사용할 수 있는 명령이다. 의외로 자주 사용했던 명령어라 따로 정리를 했다.

다음과 같은 문법으로 사용된다.

>  :[*range*]s[ubstitute]/{*pattern*}/{*string*}/[*flags*] \[*count*]
>
>  :[*range*]s[ubstitute],{*pattern*},{*string*},[*flags*] \[*count*]

해당 범위 내의 문자들에 대해 pattern에 해당하는 내용이 string으로 대체된다.

flags에 해당하는 옵션은 다음과 같다.

- g : global. 범위 내에서 검색된 모든 문자열을 교체한다. 기본적으로는 라인에서 처음 만나는 패턴만 교체한다.
- i : ignore. 대소문자를 무시한다.
- c : confirm. 교체 시마다 교체 여부를 확인한다. 각각의 하위 옵션은 다음과 같다.
  - y : yes.
  - n : no.
  - a : all.
  - q : quit.
  - l : line. 현재 라인만 교체하고 끝낸다.
  - ^E : 아래로 한 라인을 스크롤 하여 보여준다.
  - ^Y : 위로 한 라인을 스크롤 하여 보여준다.
- e : error. 교체 중 에러를 무시하며 에러 메세지도 표시하지 않는다.

