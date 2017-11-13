---
layout: post
title: Class
category: python
tags: python
---

&nbsp;

# Class

클래스는 다음의 문법으로 정의한다.

```python
class name:
    # Memvber Variables
    # Member Methods
```

클래스 객체는 독립적인 namespace를 갖는다. 클래스 인스턴스도 각각 독립적인 namespace를 갖는다. 변수나 함수 이름을 찾을 때 인스턴스 객체 -> 클래스 객체 -> 전역 순으로 찾는다.

파이썬에서는 클래스에 대한 기본 접근 권한을 public으로 한다.

파이썬에서는 런타임에 클래스나 인스턴스에 멤버 변수를 추가, 삭제할 수 있다.

##### 생성자 & 소멸자

생성자, 소멸자는 각각 `__init__()`, `__del__()` 함수로 정의되어 있다. 변경을 원하면 재정의하면 된다.

생성자는 인스턴스가 생성될 때 호출되며, 소멸자는 인스턴스의 레퍼런스 카운터가 0이 될 때 호출된다.

##### Static Method & Class Method

인스턴스 없이 클래스를 통해 직접 호출할 수 있는 메서드들이다. 정적 메서드는 인자가 필요없고, 클래스 메서드는 암묵적으로 첫 인자로 클래스 객체가 전달된다.

다음의 문법으로 사용된다.

>Called by MethodName = **staticmethod**(MethodName in Class)
>
>Called by MethodName = **classmethod**(MethodName in Class)

실제 사용 예는 다음과 같다.

```python
class Counter:
    counter = 0
    
    def __init__(self):
        Counter.counter += 1
        
    def staticPrintCounter():
        print("Counter: ", Counter.counter)
    SPrintCounter = staticmethod(staticPrintCounter)
        
    def classPrintCounter(cls):
        print("Counter: ", cls.counter)
	CPrintCounter = classmethod(classPrintCounter)
    
a, b, c = Counter(), Counter(), Counter()
Counter.SPrintCounter()
b.SPrintCounter()
Counter.CPrintCounter()
b.CPrintCounter()
```

