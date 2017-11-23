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

formatter에 이름 혹은 딕셔너리를 사용할 수도 있다.

```python
print("{item} is {color}".format(item='apple', color='red'))        

test = {'item':'apple', 'color':'red'}
print("{0[item]} is {0[color]}".format(test))

item = 'apple'
color = 'red'
print("{0[item]} is {0[color]}".format(locals()))
```

formatter에 '**' 기호를 사용하면 딕셔너리로 간주되고 인자를 하나만 받게 된다.

```python
test = {'item':'apple', 'color':'red'}
print("{item} is {color}".format(**test))
```

formatter에 리스트와 같이 인덱스를 사용하는 변수도 사용할 수 있다.

```python
numbers = [1, 2, 3, 4, 5]
print("{numbers[1]}".format(**vars()))
```

formatter에 클래스의 변수도 사용할 수 있다.

```python
class testClass:
    var = 3.14
c = testClass()
print("{c.var}".format(**vars()))
```

formatter를 사용하면서 정렬, 폭, 부호, 공백을 처리할 수 있다.

```python
# ':' 이후의 문자로 공백을 채운다.
# > : 우측 정렬
# < : 좌측 정렬
# ^ : 가운데 정렬
# 정렬 이후의 숫자는 출력 폭을 나타낸다.
>>> print("{0:@>5}".format(10))
@@@10
# = : 부호를 표시하고 출력 폭을 고려하여 공백 표시를 한 후 출력될 값을 출력한다.
# + : 플러스 부호도 표시, 마이너스 부호도 표시
# - : 마이너스 부호만 표시
# 공백 : 플러스 부호는 공백으로 표시, 마이너스 부호는 표시
>>> print("{0:@=+5}".format(10))
+@@10
>>> print("{0:@>+5}".format(-10))
@@-10
>>> print("{0:@>-5}".format(-10))
@@-10
>>> print("{0:@> 5}".format(10))
@@ 10
>>> print("{0:@> 5}".format(-10))
@@-10
```

formatter로 다른 진수로 변환하여 출력할 수도 있다.

```python
>>> print("{0:b}, {0:o}, {0:d}, {0:x}".format(10))
1010, 12, 10, a
>>> print("{0:c}".format(65))
A
>>> print("{0:#b}, {0:#o}, {0:#d}, {0:#x}".format(10))
0b1010, 0o12, 10, 0xa
```

formatter로 실수도 표시할 수 있다.

```python
>>> print("{0:f}, {0:e}, {0:%}".format(4 / 3))
1.333333, 1.333333e+00, 133.333333%
# 소수부의 자리수를 지정해줄 수 있다.
>>> print("{0:.3f}".format(4 / 3))
1.333
```

