---
layout: post
title: Regular Expression
category: vim
tags: vim
---

&nbsp;

# Regular Expression

## POSIX Standard Regular Expression

### Meta Characters

- 문자 지정

  - . : 임의의 문자 하나.

- 반복 지정

  - ? : 문자 패턴이 0 or 1.
  - \+ : 문자 패턴이 1개 이상 반복.
  - \* : 문자 패턴이 0개 이상 반복.
  - {...} : 문자 패턴 반복 수를 지정.
    Ex) {3}, {,5}, {3, 7}

- 위치 지정

  - ^ : 행의 맨 앞.
  - $ : 행의 맨 끝.

- 그룹 지정

  - [...] : 대괄호 안의 문자 중 한 문자.
  - [^...] : 대괄호 안에 지정된 문자를 제외한 나머지.

- 기타

  - \ : Escape 문자.
  - | : Or.
  - () : 패턴을 그룹화하거나 백 레퍼런스로 작동.
    백 레퍼런스는 정규 표현식으로 매칭된 결과 값을 저장해두었다가 변수처럼 사용할 수 있는 기능이다.

&nbsp;

### Character Class

- [[:alnum:]] : 알파벳과 숫자
- [[:alpha:]] : 알파벳 대소문자
- [[:upper:]] : 알파벳 대문자
- [[:lower:]] : 알파벳 소문자
- [[:digit:]] : 10진수 숫자
- [[:xdigit:]] : 16진수 숫자
- [[:cntrl:]] : 제어 문자
- [[:space:]] : \<TAB>, \<CR>, \<LF>
- [[:blank:]] : \<TAB>
- [[:gra ph:]] : 공백을 제외한 문자
- [[:print:]] : 출력 가능한 문자
- [[:punct:]] : 출력 가능한 특수 문자



