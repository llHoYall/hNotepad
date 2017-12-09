---
layout: post
title: Module - fractions
category: python
tags: python
---

&nbsp;

# Module - fractions

유리수와 관련된 모듈이다. 유리수는 두 정수의 분수 형태로 나타낼 수 있는 실수를 말한다.

#### Methods

- **Fraction(*x*, *y*)** : x를 분자, y를 분모로 하는 유리수 객체를 생성한다.
- **Fraction(*fraction*)** : fraction 객체를 입력받아 유리수 객체를 생성한다.
- **Fraction(*string*)** : 문자열을 입력받아 유리수 객체를 생성한다.
- **from_float(*flt*)** : 실수 값을 입력받아 유리수 객체를 생성한다.
- **from_decimal(*dec*)** : 10진수 값을 입력받아 유리수 객체를 생성한다.
- **limit_denominator(max_denominator=1000000)** : 입력받은 분모의 최대값을 넘지 않는 가장 가까운 유리수 객체를 반환한다.
- **\_\_floor\_\_()** : 해당 유리수를 넘지 않는 가장 큰 정수를 반환한다. (내림) math.floor() 메서드에 의해 호출된다
- **\_\_ceil\_\_()** : 해당 유리수를 넘지 않는 가장 작은 정수를 반환한다. (올림) math.ceil() 메서드에 의해 호출된다.
- **\_\_round\_\_([*ndigits*])** : 반올림해서 가장 가까운 정수를 반환한다. math.round() 메서드에 의해 호출된다.
- **gcd(*a*, *b*)** : 두 정수 사이의 최대 공약수를 반환한다.

