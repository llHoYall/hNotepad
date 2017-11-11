---
layout: post
title: Flow Control
category: python
tags: python
---

&nbsp;

# Flow Control

### if

```python
if condition:
    statements
elif condition:
    statements
else:
    statements
```

조건문은 다음과 같이 범위 지정도 간편하게 할 수 있다.

```python
>>> score = 70
>>> if 50 <= score <= 100:
    	grade = "A"
    else:
        grade = "B"
```

다음과 같이 한 줄 조건문도 가능하다.

```python
>>> money = 10
>>> item = "apple" if money > 10 else "banana"
```

조건을 판단할 때, <정수 0, 실수 0.0, 빈 시퀀스 (), [], {}, 빈 문자열 '', None> 은 False로 판단한다.

조건문은 단축 평가 (short circuit evaluation) 된다.

&nbsp;

### pass

pass는 아무동작도 수행하지 않음을 명시적으로 나타낼 때 사용한다.