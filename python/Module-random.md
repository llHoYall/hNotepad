---
layout: post
title: Module - random
category: python
tags: python
---

&nbsp;

# Module - random

#### Methods

- **seed([*x*])** : 인자가 생략되거나 None인 경우, 현재 시스템 시간 값을 사용한다.
- **random()** : '0.0 <= f < 1.0'인 임의의 실수를 반환한다.
- **uniform(*a*, *b*)** : 인자로 받은 두 값 사이의 임의의 float 숫자를 반환한다.
- **gauss(*m*, *sb*)** : 평균이 m, 표준편차가 sb인 정규분포의 임의의 숫자를 반환한다.
- **randrange([*start*, ]*stop*[, *step*])** : range()의 아이템 중에서 임의의 아이템을 반환한다.
- **randint(*a*, *b*)** : 'a <= N <= b'인 임의의 정수를 반환한다.
- **choice(*seq*)** : 입력받은 시퀀스 객체의 임의의 아이템을 반환한다. 인자가 없을 경우 IndexError 예외가 발생한다.
- **shuffle(*x*[, *random*])** : 입력받은 시퀀스 객체를 섞는다.
- **sample(*population*, *k*)** : k개 만큼의 아이템을 시퀀스나 셋 객체로부터 임의로 중복없이 추출한다. 원본에는 아무런 변경을 가하지 않는다.