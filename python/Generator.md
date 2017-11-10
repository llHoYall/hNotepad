---
layout: post
title: Generator
category: python
tags: python
---

&nbsp;

# Generator

제너레이터는 이터레이터를 만들 수 있다.

`return` 대신 `yield`를 사용한다. `yield`를 만나면 수행을 잠시 멈추고 해당 루틴을 호출한 곳에 값을 전달한다. 다시 호출한 곳에서 `next()`를 호출하면 제너레이터는 중단된 곳에서부터 다시 시작한다.

또한, 데이터를 미리 생성해놓지 않고 필요 시마다 생성을 하기 때문에 메모리가 절약된다.

사용 예는 다음과 같다.

```python
>>> def gen():
    	data = [1, 2, 3]
        for i in data:
            yield i
>>> it = iter(gen())
>>> next(it)
1
>>> next(it)
2
```

```python
>>> a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]		# need memories
>>> sum(a)
55
>>> b = (i for i in range(11))		# don't need memories
>>> sum(b)
55
```



