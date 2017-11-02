---
layout: post
title: Datatype Number
category: python
tags: python
---

&nbsp;

# Datatype - Number

### int

정수형의 기본은 10진수이다. 즉, 숫자를 사용하면 10진수로 인식된다. 

다른 진수를 사용하려면 각각 2진수는 '0b', 8진수는 '0o', 16진수는 '0x'를 붙여준다.

10진수를 다른 진수로 변환하려면 다음 함수를 사용한다.

```python
>>> 0b10
2
>>> 0o10
8
>>> 0x10
16
>>> bin(10)
'0b1010'
>>> oct(10)
'0o12'
>>> hex(10)
'0xa'
```

&nbsp;

### float

실수형은 소수점을 사용하거나 지수형을 사용할 수 있다.

- 소수점 : 3.14
- 지수형 : 314e-2

&nbsp;

### complex

복소수는 다음과 같은 표현을 사용한다.

```python
>>> x = 3 - 7j
>>> x.real
3.0
>>> x.imag
-7.0
>>> x.conjugate()
(3+7j)
```

