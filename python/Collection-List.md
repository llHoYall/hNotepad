---
layout: post
title: Collection List
category: python
tags: python
---

&nbsp;

# Collection - List

리스트는 값의 나열이며, 여러 종류의 값을 담을 수 있다.

인덱싱이 가능하며 슬라이싱도 가능하다.

- 순서가 존재한다.
- 중복이 가능하다.

&nbsp;

### Create

```python
color = ['red', 'green', 'blue']
listA = list([1, 2, 3])
listB = list({4, 5, 6})
listC = list((7, 8, 9))
```

&nbsp;

### Add

```python
# 맨 뒤에 추가된다.
colors.append('gold')
# 인덱스의 위치에 추가된다.
colors.insert(1, 'black')
# 맨 뒤에 한 번에 추가된다.
colors.extend(['white', 'gray'])
# extend()와 동일하게 맨 뒤에 추가된다.
# 리스트가 아닌 문자열을 더하면 한 글자씩 추가된다.
colors += ['red']
```

&nbsp;

### Get

```python
# 해당 값이 처음 나온 인덱스를 반환한다.
colors.index('red')
# 해당 인덱스 뒤쪽에서 값이 처음 나온 인덱스를 반환한다.
colors.index('red', 1)
# 해당 인덱스의 사이에서 값이 처음 나온 인덱스를 반환한다.
# 값이 없을 경우 에러가 발생한다.
colors.index('red', 1, 5)
# 리스트에서 해당 값의 개수를 반환한다.
colors.count('red')
```

&nbsp;

### Check

```python
>>> 1 in listA
True
```

&nbsp;

### Remove

```python
# 맨 뒤에 있는 값을 하나 반환하며 리스트에서 삭제된다.
colors.pop()
# 해당 인덱스의 값을 반환하며 리스트에서 삭제된다.
colors.pop(1)
# 해당 값을 삭제한다.
# 동일한 값이 있다면 앞쪽에 있는 값을 삭제한다.
colors.remove('green')
```

&nbsp;

### Sort

```python
# 오름차순으로 정렬한다.
colors.sort()
# 내림차순으로 정렬한다.
colors.reverse()
# 키로 지정된 함수로 정렬을 하며, 역순 지정을 할 수 있다.
colors.sort(key=func, reverse=True)
```

