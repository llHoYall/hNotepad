---
layout: post
title: Variable
category: python
tags: python
---

&nbsp;

# Variable

### Naming Convention

변수명은 문자, 숫자, underbar로 구성되며, 숫자로 시작되면 안된다.

파이썬의 변수명은 대소문자를 구별한다.

키워드는 변수명으로 사용할 수 없다.

&nbsp;

### Copy

파이썬에서도 shallow copy와 deep copy가 존재한다. 

- 얕은 복사는 객체를 공유한다. 즉, 같은 객체를 가리킨다.
- 깊은 복사는 객체를 공유하지 않고 각각 다른 객체를 가리킨다.

리스트의 경우 다음과 같이 한다.

```python
a = [1, 2, 3]
b = a		# shallow copy
b = a[:]	# deep copy
```

리스트 이외의 일반적인 경우는 다음과 같이 한다.

```python
>>> import copy
>>> a = [1, [2, 3]]
>>> b = copy.copy(a)
>>> c = copy.deepcopy(a)
>>> id(a), id(b), id(c)		# 전부 다름.
>>> a[1].append(4)
>>> a, b, c							# a, b는 같고 c는 다름.
>>> id(a[1]), id(b[1]), id(c[1])	# a, b는 같고 c는 다름.
```

&nbsp;

### Identity

id() 함수를 사용하여 객체의 identity를 확인할 수 있다.

```python
>>> a = [1, 2, 3]
>>> id(a)
```

&nbsp;

### Keyword

- and
- as
- assert
- break
- class
- continue
- def
- del
- elif
- else
- except
- is
- finally
- for
- from
- global
- if
- import
- in
- is
- lambda
- nonlocal
- not
- or
- pass
- raise
- return
- try
- while
- with
- yield

