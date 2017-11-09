---
Controllayout: post
title: Function Lambda
category: python
tags: python
---

&nbsp;

# Function - Lambda

람다 함수는 레퍼런스 이름 없이 객체만 존재하는 함수이다.

- 여러 개의 인자를 전달받을 수 있다.
- return문은 사용할 수 없다. 람다 함수의 실행 결과가 곧 반환 값이다.

람다 함수는 다음의 문법을 따른다.

```python
lambda args : statements
```

##### Example

```python
>>> adder = lambda x, y : x + y
>>> adder(2, 3)
5
>>> (lambda x : x * x)(3)
9
```

