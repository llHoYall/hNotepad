---
layout: post
title: doctest
category: python
tags: python
---

&nbsp;

# doctest

주석을 사용하여 test를 할 수 있다.

```python
# div.py

def div(x, y):
    """ 
    This function is to divide x into y.
    
    [test]
    >>> div(1, 2)
    0.5
    >>> div(4, 3)
    1.333333333333    
   	>>> div(-1, 4)
   	-0.25
    """
    return x / y

if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

main내용 없이 div() 함수만 있더라도, 다음과 같이 테스트가 가능하다.

> $ python -m doctest div.py -v

doctest는 정상 통과될 경우 아무런 메시지도 출력되지 않으므로 `-v`옵션을 넣어 수행 과정을 출력하도록 했다.

```python
# test.txt

This function is to divide x into y.
    
[test]
>>> from div import *
>>> div(1, 2)
0.5
>>> div(4, 3)
1.333333333333    
>>> div(-1, 4)
-0.25

# div.py

def div(x, y):
    return x / y

if __name__ == "__main__":
    import doctest
    doctest.testfile('test.txt')
```

위 예제와 같이 주석을 별도의 파일로 저장하여 로드하는 방법으로도 doctest를 사용할 수 있다.

