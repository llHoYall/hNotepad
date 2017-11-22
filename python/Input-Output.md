---
layout: post
title: Input/Output
category: python
tags: python
---

&nbsp;

# Input/Output

### Output

화면 출력은 `print()` 함수를 사용한다.

```python
>>> print('Hello' 'World' '!')
HelloWorld!
>>> print('Hello', 'World', '!')
Hello World !
>>> print('Hello' + 'Python' + '!')
HelloPython!
```

인자로 구분자(sep), 끝라인(end), 출력(file)을 지정할 수 있다. 기본 값은 각각 공백, '\n', sys.stdout 이다.

```python
import sys
print('Welcome to', 'Python', sep='~', end='!', file=sys.stderr)
```

다음과 같이 formatter를 사용할 수 있다.

```python
for n in [2, 3, 4, 5, 6, 7, 8, 9]:
    print("-- Table {0} --".format(n))
    for i in [1, 2, 3, 4, 5, 6, 7, 8, 9]:
        print("{0} * {1} = {2}".format(n, i, n * i))
```

