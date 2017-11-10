---
layout: post
title: Built-In Function
category: python
tags: python
---

&nbsp;

# Built-In Function

- **dir([*object*])**
  인자 없이 사용하면 현재 local scope에 있는 이름의 목록을 보여준다.
  인자와 함께 사용하면 해당 객체에 있는 유효한 attributes 목록을 보여준다.
- **globals()**
  생성된 함수 객체를 보여준다.
- **help([*object*])**
  해당 객체의 도움말을 보여준다.
- **id(*object*)**
  객체의 identity를 보여준다.
- **iter(*object*[, *sentinel*])**
  이터레이터 객체를 반환한다.
- **map(*function*, *iterable*, ...)**
  이터레이터의 각 아이템에 함수를 적용하여 반환한다. 반환값은 yielding 된다.
- **next(*iterator*[, *default*])**
  이터레이터의 \__next\__() 메서드를 호출하여 다음 아이템을 얻는다. *default*를 명시하면 이터레이터가 고갈되면 *default*가 반환된다.
- **sum(*iterable*[, *start*])**
  iterable item의 start부터 왼쪽에서 오른쪽으로 합계를 구한다.


