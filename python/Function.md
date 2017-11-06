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

파이썬에서 인자는 레퍼런스를 이용해 전달하지만, C/C++에서의 call-by-reference와는 다르다. 

return은 함수를 종료하고, 호출한 곳으로 되돌아가게 한다. return이 없다면 None을 반환하고, return만 있어도 None을 반환한다.

