---
layout: post
title: Function
category: python
tags: python
---

&nbsp;

# Function

파이썬에서는 함수도 객체이다.

함수는 다음과 같이 선언한다.

```python
def func_name(param1, param2, ..., paramN):
    statements
    [return ret_value]
```

함수 이름은 함수 객체를 참조하는 레퍼런스이다. 함수 레퍼런스는 다른 변수에 할당할 수 있다.

&nbsp;

### Parameter

##### Passing Argument

파이썬에서 인자는 레퍼런스를 이용해 전달하지만, C/C++에서의 call-by-reference와는 다르다. 

- Immutable Variable
  ```python
  >>> a = 10
  >>> b = 20
  >>> def sum1(x, y):
      	return x + y
  >>> sum1(a, b)
  30

  >>> x = 10
  >>> def sum2(x, y):
      	x = 1
          return x + y
  >>> sum2(x, b)
  21
  >>> x
  10
  ```
  변경 불가능한 변수를 전달할 경우, 함수 내부의 변경이 외부에 영향을 미치지 않는다. 즉, 함수 내부에서 1이라는 객체가 생성되고 x에 레퍼런스가 할당된 후, 함수를 빠져나오면 x는 원래의 10이라는 객체를 가리킨다.

- Mutable Variable

  ```python
  >>> def change1(x):
      	x[0] = 'H'
  >>> word = ['J', 'A', 'M']
  >>> change1(word)
  >>> word
  ['H', 'A', 'M']

  >>> def change2(x):
      	x = x[:]
          x[0] = 'H'
          return None
  >>> word = ['J', 'A', 'M']    
  >>> change2(word)
  >>> word
  ['J', 'A', 'M']
  ```

  변경 가능한 변수를 전달할 경우, 함수 내부의 변경이 외부에 영향을 미친다. 이것을 원치 않을 경우 변경 불가능한 변수의 예처럼 함수 내에서 새로운 객체를 레퍼런스 하게 하면 된다.

##### Default Parameter

함수 호출 시 인자를 지정하지 않아도 기본 값이 할당되게 한다.

```python
>>> def add(a, b=2):
    	return a + b
>>> add(3)
5
```

##### Keyword Parameter

인자의 이름으로 값을 전달한다.

```python
>>> def connect(server, port):
    	str = "http://" + server + ":" + port
    	return str
>>> connect("example.com", "8080")
'http://example.com:8080'
>>> connect(port="8080", server="example.com")
'http://example.com:8080'
>>> connect("example.com", port="8080")
'http://example.com:8080'
>>> connect(server="example.com", "8080")
SyntaxError: positional argument follows keyword argument
```

##### Variable Argument

함수 선언 시 *를 인자 앞에 붙이면 개수가 정해지지 않은 가변 인자를 전달받는다. 입력받은 인자들은 내부적으로 튜플에 저장한다.

```python
>>> def var_sum(*args):
    	return sum(args)
>>> var_sum(1, 2, 3)
6
```

함수 선언 시 **를 인자 앞에 붙이면 딕셔너리 형태로 인자를 받을 수 있다.

```python
>>> def userURIBuilder(server, port, **kwargs):
    	str = "http://" + server + ":" + port + "/?" 
        for k in kwargs.keys():
            str += k + "=" + kwargs[k] + "&"
        return str
>>> userURIBuilder("example.com", "8080", id='hoya', passwd='1234')
'http://example.com:8080/?id=hoya&passwd=1234&'
```

&nbsp;

### Return

return은 함수를 종료하고, 호출한 곳으로 되돌아가게 한다. return이 없다면 None을 반환하고, return만 있어도 None을 반환한다.

&nbsp;

### Scoping Rule

함수 내부는 별도의 namespace를 갖는다. 

함수 내부를 local scope라고 한다. 함수 밖을 global scope라고 하며, 파이썬 자체에서 정의된 영역을 built-in scope라고 한다.

변수나 함수 등의 이름을 참조할 때, 이름을 검색하는 규칙이 있는데 이것을 'LGB 규칙'이라고 한다. 순서대로 Local -> Global -> Built-In scope에서 참조를 하게 된다.

Local scope에서 global scope에 있는 이름을 참조하고 싶다면 **global** 키워드를 이용하여 선언해준다.