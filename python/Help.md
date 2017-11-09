---
layout: post
title: Help
category: python
tags: python
---

&nbsp;

# Help

내장 함수인 `help()`를 사용하여 REPL 상에서 도움말을 볼 수 있다. 

함수, 클래스, 모듈 등 모든 객체의 기본 도움말을 보여준다. 예를 들어, `print()` 함수의 도움말을 보려면 다음과 같이 한다.

```python
help(print)
```

사용자가 정의한 함수 등에서도 이 기능을 사용할 수 있다.

객체의 `__doc__` 속성에 설명을 적거나 직접 함수 등의 선언부에 `"""` 기호를 사용하여 적어주면 된다.

```python
adder.__doc__ = "blah blah"
def user_func(x):
    """
    blah blah
    """
    return x
```

