---
layout: post
title: Collection Tuple
category: python
tags: python
---

&nbsp;

# Collection - Tuple

튜플은 리스트와 유사하지만 읽기 전용이다. 따라서 속도가 빠르다.

- 순서가 존재한다.
- 중복이 가능하다.

&nbsp;

### Create

```python
numbers = (1, 2, 3)
a, b = 1, 2		# (a, b) = (1, 2)
tupleA = tuple([1, 2, 3])
tupleB = tuple({4, 5, 6})
tupleC = tuple((7, 8, 9))
```

&nbsp;

### Get

```python
# 해당 값의 개수를 반환한다.
tupleA.count(2)
# 해당 값이 처음 나온 인덱스를 반환한다.
tupleA.index(3)
```

&nbsp;

### Check

```python
>>> 1 in tupleA
true
```

&nbsp;

### Operation

```python
# Swap
a, b = b, a
```

