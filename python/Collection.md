---
layout: post
title: Collection
category: python
tags: python
---

&nbsp;

# Collection

컬렉션에는 튜플, 리스트, 셋, 딕셔너리가 있다.

각 컬렉션끼리는 생성자 함수를 통해 상호 변환이 가능하다.

```python
tupleA = tuple([1, 2, 3])
tupleB = tuple({1, 2, 3})
listA = list((7, 8, 9))
listB = list({4, 5, 6})
setA = set([1, 2, 3])
setB = set((7, 8, 9))
```

각 컬렉션끼리는 혼용해서 사용할 수 있다.

```python
{'keyA': 35.1, 'keyB': [1, 2, 3], 'keyC': {'abc': 123, 'def': 456}}
[1, 2, 3, ('red', 'green'), {'banana': 'yellow'}]
```

