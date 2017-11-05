---
layout: post
title: Collection Set
category: python
tags: python
---

&nbsp;

# Collection - Set

세트는 집합과 동일하다. 리스트와 마찬가지로 값의 나열이다.

- 순서가 없다.
- 중복이 불가능하다.

&nbsp;

### Create

```python
numbers = {1, 2, 3}
setA = set([1, 2, 3])
setB = set({4, 5, 6})
setC = set((7, 8, 9))
```

&nbsp;

### Check

```python
>>> 1 in setA
True
```

&nbsp;

### Operation

```python
# 합집합
setA | setB
setA.union(setB)
# 교집합
setA & setB
setA.intersection(setB)
# 차집합
setA - setB
```

