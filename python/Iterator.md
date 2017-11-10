---
layout: post
title: Iterator
category: python
tags: python
---

&nbsp;

# Iterator

시퀀스, 문자열 등 순회 가능한 객체는 이터레이터라는 객체가 포함되어 있다.

`iter()` 함수를 사용하면 순회 가능한 객체에서 이터레이터를 얻을 수 있고, `next()` 함수를 사용하여 이터레이터의 다음 요소를 얻을 수 있다. `next()` 함수는 결국 이터레이터의  `__next__()` 메서드를 호출하는 것이다. 이터레이터의 끝에 도달하면 StopIteration 예외를 반환한다.

사용 예는 다음과 같다.

```python
>>> l = [1, 2, 3]
>>> it = iter(l)
>>> next(it)
1
>>> it.__next__()
2
>>> next(it)
3
>>> next(it)
...
StopIteration
```

