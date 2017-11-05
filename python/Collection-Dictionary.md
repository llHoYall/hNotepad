---
layout: post
title: Collection Dictionary
category: python
tags: python
---

&nbsp;

# Collection - Dictionary

딕셔너리는 키와 값의 쌍으로 구성되어 있다.

- 순서가 없다.
- 중복이 불가능하다.

&nbsp;

### Create

```python
dictA = dict(a = 1, b = 2, c = 3)
example = {'apple': 'red', 'banana': 'yellow'}
```

&nbsp;

### Add

```python
# 새로운 키, 값 쌍을 정의하여 추가할 수 있다.
example['grape'] = 'purple'
# 기존에 있는 키를 사용하여 값을 재정의 할 수 있다.
example['apple'] = 'green'
```

&nbsp;

### Get

```python
# key를 인덱스로 사용하여 값을 얻는다.
example['apple']
# 키, 값 쌍을 반복가능한 튜플들의 dict_items 클래스 객체로 얻는다
for c in example.items():
for k, v in example.items():
# 키를 반복 가능한 dict_keys 클래스 객체로 얻는다.
for k in example.keys():
# 값을 반복 가능한 dict_values 클래스 객체로 얻는다.
for v in example.values():
```

&nbsp;

### Remove

```python
# 해당 키, 값 쌍을 제거한다.
del example['apple']
# 딕셔너리의 모든 키, 값 쌍을 삭제한다
example.clear()
```

