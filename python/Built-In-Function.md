---
layout: post
title: Built-In Function
category: python
tags: python
---

&nbsp;

# Built-In Function

- **abs(*x*)**
  인자의 절대값을 반환한다.

- **dir([*object*])**
  인자 없이 사용하면 현재 local scope에 있는 이름의 목록을 보여준다.
  인자와 함께 사용하면 해당 객체에 있는 유효한 attributes 목록을 보여준다.

- **divmod(*a*, *b*)**
  ​a / b의 몫과 나머지를 튜플로 반환한다.

- **enumerate(*iterable*, start=0)**
  (인텍스, 아이템)형태의 튜플의 리스트가 반환된다.

- **filter(*function*, *iterable*)**
  iterable 객체의 아이템 중 function의 결과가 True인 아이템만 묶어 이터레이션 객체를 반환한다. 결과를 튜플, 리스트, 딕셔너리 등으로 사용하려면, tuple(), list(), dict() 함수를 사용해야한다.
  함수에 None을 사용하면 아무런 필터링도 하지 않는다.

- **globals()**
  생성된 함수 객체를 보여준다.

- **help([*object*])**
  해당 객체의 도움말을 보여준다.

- **locals()**
  현재 로컬 심벌 테이블을 딕셔너리로 반환한다.

- **id(*object*)**
  객체의 identity를 보여준다.

- **isinstance(*object*, *classinfo*)**
  object가 classinfo의 인스턴스이면 True, 아니면 False를 반환한다.
  classinfo에는 튜플 형태로 여러 개를 넣을 수 있다.

- **issubclass(*class*, *classinfo*)**
  class가 classinfo의 서브 클래스이면 True를 반환하고 그렇지 않다면 False를 반환한다.
  클래스는 자신의 서브 클래스이다.

- **iter(*object*[, *sentinel*])**
  이터레이터 객체를 반환한다.

- **map(*function*, *iterable*, ...)**
  이터레이터의 각 아이템에 함수를 적용하여 반환한다. 반환값은 yielding 된다.

- **max(*iterable*, \*[, key, \*default])**
  이터레이터 객체의 최대값을 반환한다.

- **min(*iterable*, \*[, key, \*default])**
  이터레이터 객체의 최소값을 반환한다.

- **next(*iterator*[, *default*])**
  이터레이터의 \__next\__() 메서드를 호출하여 다음 아이템을 얻는다. *default*를 명시하면 이터레이터가 고갈되면 *default*가 반환된다.

- **pow(*x*, *y*[, *z*])**
  x의 y제곱 값을 반환한다. z가 입력될 경우 x의 y제곱한 결과를 z로 나눈 나머지(modulo)를 반환한다.

- **range([start, ]stop[, step])**
  불변하는 시퀀스 타입의 객체를 반환한다. 시작값과 증가값은 생략 시 각각 0, 1이다.

- **round(*number*[, *ndigits*])**
  인자의 반올림 결과를 반환한다. 자리수를 입력할 경우 지정된 자리수 까지 반올림 결과를 나타낸다. ndigits의 기본값은 0이다.

- **sum(*iterable*[, *start*])**
  iterable item의 start부터 왼쪽에서 오른쪽으로 합계를 구한다.

- **super([*type*[, *object-or-type*]])**
  type의 parent나 sibling class의 객체를 반환한다.
  두 번째 인자가 없을경우, unbound로 사용된다.

- **vars([*object*])**
  모듈, 클래스, 인스턴스, 다른 어떤 객체의 \_\_dict\_\_ 속성을 반환한다.

- **zip([\*]*iterables*)**
  인자로 넣은 iterable 객체의 아이템들을 하나씩 튜플로 묶어 이터레이션 객체를 반환한다. 결합을 하는 인자의 아이템의 개수가 같지 않다면 적은 쪽을 기준으로 결합한다. 결과를 튜플, 리스트, 딕셔너리 등으로 사용하려면, tuple(), list(), dict() 함수를 사용해야한다.
  iterable 객체 앞에 *를 붙이면, 결합된 객체를 분리한다.